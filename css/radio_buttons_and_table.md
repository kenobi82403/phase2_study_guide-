```html
<form action="/surveys/<%=@survey.id%>/responses" id="response_show" method="POST">
  <%@ survey.questions.map do |que| %>
<%= que.question_text%><br><br>
<% que.options.each do |opt| %>
<input type="radio" name="question[<%= que.id %>]" value="<%=opt.id%>"><%=opt.option_text %><br><br>
<%end%>
<%end%>

<input type="submit" class="link_button" value="Submit Response">
</form>
```

By giving the name attribute a specific question.id, you're grouping the radio buttons together
This is great because then you can only answer one radio button per question, but more than one radio button in one survey



Iterating through an array of SQL objects in a table

```html
<table class="user_survey_table">
  <tr>
    <th>Survey Title</th>
    <th>Date Created</th>
    <th>Survey Results</th>
    <th>Send to More People</th>
    <th>Delete Survey</th>
  </tr>
  <tr>
     <%@surveys.each do |survey|%>
     <td><%=survey.title%></td>
     <td><%=survey.created_at%></td>
     <td><a class="link_button" href="/surveys/<%= survey.id %>/results"> RESULTS</a></td>
     <td><a class="link_button" href='#'> SEND TO MORE PEOPLE</a></td>

     <td><form action="/surveys/<%=survey.id%>" method="POST">
      <input type="hidden" name="_method" value="DELETE">
      <input type="submit" class="link_button" value="Delete Survey"></form></td>
    </tr>
     <%end%>
</table>
```
