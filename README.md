# rest-api
// create class CtoFservice.java

public class CtoFService { 
@GET 
@Produces("application/xml") 
public String convertCtoF() { 
Double fahrenheit; 
Double celsius = 36.8; 
fahrenheit = ((celsius * 9) / 5) + 32; 
String result = "@Produces(\"application/xml\") Output: \n\nC to F Converter Output: \n\n" + fahrenheit; 
return "<ctofservice>" + "<celsius>" + celsius + "</celsius>" + "<ctofoutput>" + result + "</ctofoutput>" + "</ctofservice>"; 
} 
@Path("{c}") 
@GET 
@Produces("application/xml") 
public String convertCtoFfromInput(@PathParam("c") Double c) { 
Double fahrenheit; 
Double celsius = c; 
fahrenheit = ((celsius * 9) / 5) + 32; 
String result = "@Produces(\"application/xml\") Output: \n\nC to F Converter Output: \n\n" + fahrenheit; 
return "<ctofservice>" + "<celsius>" + celsius + "</celsius>" + "<ctofoutput>" + result + "</ctofoutput>" + "</ctofservice>"; 
} 
} 

// create class FtoCservice.java 

public class FtoCService { 
@GET 
@Produces("application/json") 
public Response convertFtoC() throws JSONException { 
JSONObject jsonObject = new JSONObject(); 
Double fahrenheit = 98.24; 
Double celsius; 
celsius = (fahrenheit - 32)*5/9; 
jsonObject.put("F Value", fahrenheit); 
jsonObject.put("C Value", celsius); 
String result = "@Produces(\"application/json\") Output: \n\nF to C Converter Output: \n\n" + jsonObject; 
return Response.status(200).entity(result).build(); 
} 
@Path("{f}") 
@GET 
@Produces("application/json") 
public Response convertFtoCfromInput(@PathParam("f") float f) throws JSONException { 
JSONObject jsonObject = new JSONObject(); 
float celsius; 
celsius = (f - 32)*5/9; 
jsonObject.put("F Value", f); 
jsonObject.put("C Value", celsius); 
String result = "@Produces(\"application/json\") Output: \n\nF to C Converter Output: \n\n" + jsonObject; 
return Response.status(200).entity(result).build(); 
} } 
