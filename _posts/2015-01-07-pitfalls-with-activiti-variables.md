---
layout: post
title: Pitfalls with getting Acitviti variable value
date: '2015-01-07T16:00:00.000+02:00'
tags: activiti
---
Today I was doing unit tests for one Activiti flow. In the end of the test I wanted to assert value of output variable of that flow.

To set the variable, you can do it in following ways:
* Do it in the script: 
~~~
...
execution.setVariable("finalStatus", "OK")
...
~~~
* User service task, which puts service result in execution variable
* In java service delegate again using: 
~~~
execution.setVariable("finalStatus", "OK")
~~~

In order to test variable, we need to use history service:
~~~
    @SuppressWarnings("unchecked")
	protected <T> T fetchVariable(ProcessInstance processInstance, String variableName) {
		return (T) activitiRule
		    .getHistoryService()
		    .createHistoricVariableInstanceQuery()
		    .variableName(variableName)
			.processInstanceId(processInstance.getId())
			.singleResult().getValue();
	}
~~~

Basically as the flow execution is finished, the only way we can obtain value of the variable is to use HistoryService and to do query by processInstanceId and variable name.

All is good and well, untill actually in your flow you do multiple assignments to same variable. I was having problems, as there were multiple history entries. Apparently Activiti saves full history of changes. So in order to get last value (if presumably this is what you need), code needs to be changed.
~~~
    @SuppressWarnings("unchecked")
	protected <T> T fetchVariable(ProcessInstance processInstance, String variableName) {
		List<HistoricVariableInstance> list = activitiRule
		    .getHistoryService()
		    .createHistoricVariableInstanceQuery()
		    .variableName(variableName)
			.processInstanceId(processInstance.getId())
			.list();
		if (list.size() == 0) {
			return null;
		} else {
			return (T) list.get(list.size() - 1).getValue();
		}
	}
~~~
