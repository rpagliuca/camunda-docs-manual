---

title: "Get Identity-Link"
weight: 10

menu:
  main:
    name: "Get List"
    identifier: "rest-api-history-get-identity-link-query"
    parent: "rest-api-history-identity-links"
    pre: "GET `/history/identity-links`"

---


Query for historic identity link that fulfill given parameters.
The size of the result set can be retrieved by using the [get identity-links count]({{< relref "reference/rest/history/identity-links/get-identity-link-query-count.md" >}}) method.


# Method

GET `/history/identity-links`


# Parameters

## Query Parameters

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>identityLinkId</td>
    <td>Restricts to identity links that has the given id.</td>
  </tr>
  <tr>
    <td>identityLinkType</td>
    <td>Restricts to identity links that have the given type.</td>
  </tr>
  <tr>
    <td>userId</td>
    <td>Restricts to identity links that have the given user id.</td>
  </tr>
  <tr>
    <td>groupId</td>
    <td>Restricts to identity links that have the given group id.</td>
  </tr>
  <tr>
    <td>dateBefore</td>
    <td>Restricts to identity links that have the time before the given time.</td>
  </tr>
  <tr>
    <td>dateAfter</td>
    <td>Restricts to identity links that have the time after the given time</td>
  </tr>
  <tr>
    <td>taskId</td>
    <td>Restricts to identity links that have the given task id.</td>
  </tr>
  <tr>
    <td>processDefId</td>
    <td>Restricts to identity links that have the given process definition id.</td>
  </tr>
  <tr>
    <td>operationType</td>
    <td>Restricts to identity links that have the given operationType (add/delete).</td>
  </tr>
  <tr>
    <td>assignerId</td>
    <td>Restricts to identity links that have the given assigner id.</td>
  </tr>
  <tr>
    <td>sortBy</td>
    <td>Sort the results lexicographically by a given criterion. Valid values are
    <code>identityLinkId</code>, <code>identityLinkType</code>, <code>userId</code>, <code>groupId</code>, <code>taskId</code>, <code>processDefId</code>, <code>operationType</code>, <code>assignerId</code>.
    Must be used in conjunction with the <code>sortOrder</code> parameter.</td>
  </tr>
  <tr>
    <td>sortOrder</td>
    <td>Sort the results in a given order. Values may be <code>asc</code> for ascending order or <code>desc</code> for descending order.
    Must be used in conjunction with the <code>sortBy</code> parameter.</td>
  </tr>
</table>


# Result

A JSON array of historic identity link objects.
Each historic identity link object has the following properties:

<table class="table table-striped">
  <tr>
    <th>Name</th>
    <th>Value</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>identityLinkId</td>
    <td>String</td>
    <td>Id of the Historic identity link entry.</td>
  </tr>
  <tr>
    <td>time</td>
    <td>String</td>
    <td>The time when the identity link is logged. Has the format <code>yyyy-MM-dd'T'HH:mm:ss</code>.</td>
  </tr>
   <tr>
    <td>identityLinkType</td>
    <td>String</td>
    <td>The type of identity link (candidate/assignee/owner).</td>
  </tr>
  <tr>
    <td>userId</td>
    <td>String</td>
    <td>The id of the user/assignee.</td>
  </tr>
  <tr>
    <td>groupId</td>
    <td>String</td>
    <td>The id of the group.</td>
  </tr>
  <tr>
    <td>taskId</td>
    <td>String</td>
    <td>The id of the task.</td>
  </tr>
  <tr>
    <td>processDefId</td>
    <td>String</td>
    <td>The id of the process definition.</td>
  </tr>
  <tr>
    <td>operationType</td>
    <td>String</td>
    <td>Type of operation (add/delete).</td>
  </tr>
  <tr>
    <td>assignerId</td>
    <td>String</td>
    <td>The id of the assigner.</td>
  </tr>
</table>


# Response Codes

<table class="table table-striped">
  <tr>
    <th>Code</th>
    <th>Media type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200</td>
    <td>application/json</td>
    <td>Request successful.</td>
  </tr>
  <tr>
    <td>400</td>
    <td>application/json</td>
    <td>Returned if some of the query parameters are invalid, for example if a <code>sortOrder</code> parameter is supplied, but no <code>sortBy</code>. See the <a href="{{< relref "reference/rest/overview/index.md#error-handling" >}}">Introduction</a> for the error response format.</td>
  </tr>
</table>


# Example

## Request

<!-- TODO: Insert a 'real' example -->
GET <code>/history/identity-links?taskId=aTaskId</code>

## Response

    [
      {
	    "identityLinkId": null,
        "time": "2014-03-01T08:00:00",
        "identityLinkType": "candidate",
        "userId": "aUserId",
        "groupId": "aGroupId",
        "taskId": "aTaskId",
		"processDefId": null,
        "operationType": "add",
        "assignerId": "aAssignerId"
      },
      {
	    "identityLinkId": null,
        "time": "2014-03-05T10:00:00",
        "identityLinkType": "candidate",
        "userId": "aUserId",
        "groupId": "aGroupId",
        "taskId": "aTaskId",
		"processDefId": null,
        "operationType": "delete",
        "assignerId": "aAssignerId"
      }
    ]