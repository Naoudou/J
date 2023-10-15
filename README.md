CALCULATOR


<html>
<head>
	<title> Calculator </title>
</head>
<body>
<form action="Calculator.jsp">

<br>
Enter a value for t1 <input type="text" name="t1">
<br>
Enter a value for t2 <input type="text" name="t2">
<br>
Select the operation:
 <select name="r1">  
        <option >--Select operation--</option>  
        <option value="mul">Multiplication</option>  
        <option value="add">Addition</option>  
        <option value="sub">Subtraction</option>  
        <option value="div">Division</option>  
        
  </select> 
<br><br>


		<input type="submit" value="submit">

</form>
</body>
</html>







<%@ page language="java" contentType="text/HTML" %>
<%@ page import="java.lang.*" %>

<html>

<body>
 <%
String str = request.getParameter("r1");
String str1 = request.getParameter("t1");
String str2 = request.getParameter("t2");
String operation = "";

int num1 = 0;
int num2 = 0;
int num3 = 0;

num1 =Integer.parseInt(str1);
num2 =Integer.parseInt(str2);




if(str.equals("add"))
{
  num3 = num1 + num2;
  operation = "Addition";
}
if(str.equals("sub"))
{
  num3 = num1 - num2;
  operation = "Substration";
}
if(str.equals("mul"))
{
  num3 =num1 * num2;
  operation = "Multiplication";
}
if(str.equals("div"))
{
  num3 =num1 / num2;
  operation = "Division";
}
%>

You Select : <%=operation%>
<br>
<%
out.println("OutPut:"+num3);
%>

</body>
</html>


CURRENT DATE AND TIME

<%@ page language="java" contentType="text/html"%>
<%@ page import="java.util.*"%>
<html>
<head>
<title>current date and time using jsp</title>
</head>
<body>

Date and Time:<%=(new java.util.Date())%>
</body>
</html>





FACTORIAL

<html>
<form action="Factoriel.jsp">

<br>
Enter a value for n <input type=""text" name="val">
		<input type="submit" value="SUBMIT">
</form>
</body>
</html>




<HTML>
<BODY>
<%!
	long n, result;
	String str;

	long fact(long n){
	if(n==0)
	 return 1;
	else
	 return n * fact(n-1);
}
%>

<% 
str = request.getParameter("val");
	n = Long.parseLong(str);
	result = fact(n);
%>
 <BR>
<B> Factoriel value : </B> <%=result %>

</BODY>
</HTML>



vISITORS COUNTERS



<%@ page import="java.io.*,java.util.*"%>
<html>

<body>
<form>
	<fieldset style="width:20%; background: #e6ffe6;">

		<LEGEND> JSP to count the visitor<LEGEND>
<%
		Integer hitsCount = (Integer)application.getAttribute("hitsCounter");
		if(hitsCount == null || hitsCount == 0){
			/*First Visit*/
			out.println("Welcome to my website !!");
			hitsCount = 1;
		}
		else
		{
				/*returne visit*/
				out.println("Welcome to my website !!");
				hitsCount += 1;
		}
		application.setAttribute("hitsCounter",hitsCount);
%>
		<p>Number of person visited my website : <%=hitsCount %> </p>
		
	</fieldset>

</form>
</body>
</html>




DATA FROM MYSQL


<%@page import="java.sql.*"%>

<!DOCTYPE html>
<html>
<body>

<h1>Retrieve data from database in jsp</h1>

<table border="1">
<tr>
<td>Name</td>
<td>Class</td>
<td>Place</td>
<td>Email</td>

</tr>

<%
try{
Class.forName("com.mysql.cj.jdbc.Driver");

Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/cia2","root","");
Statement statement=connection.createStatement();

ResultSet resultSet = statement.executeQuery("select * from student");
while(resultSet.next()){
%>

<tr>
<td><%=resultSet.getString("Name") %></td>
<td><%=resultSet.getString("Class") %></td>
<td><%=resultSet.getString("Place") %></td>
<td><%=resultSet.getString("Email") %></td>

</tr>

<%
}
connection.close();
} catch (Exception e) {
e.printStackTrace();
}
%>
</table> 

</body>
</html>
