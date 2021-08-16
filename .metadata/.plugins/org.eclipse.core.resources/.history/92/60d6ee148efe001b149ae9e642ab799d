package com.vmware.test;

import java.util.HashMap;
import java.util.Map;

import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class AreaController {

	@PostMapping("/calculate")
	public Response calculateArea(@RequestBody Map<String,Map<String,Object>> areaProperties)
	{
		System.out.println("Inside :"+areaProperties.size());
		int element=1;
		Response response=new Response();
		Map<String,String> result=new HashMap<>();

		if(areaProperties.size()==0)
		{
			response.setSuccessful(false);
			response.setErrorMessage("No Property provided to calculate area.");
			return response;
		}
		while(element<=areaProperties.size())
		{
			Map<String,Object> property=areaProperties.get(String.valueOf(element));
			String type=(String)property.get("type");
			if(type.equalsIgnoreCase("rectangle"))
			{
				int length=(int)property.get("l");
				int breadth=(int)property.get("b");
				long areaRectangle=(length*breadth);
				result.put(String.valueOf(element), String.valueOf(areaRectangle));
			}
			else if(type.equalsIgnoreCase("circle"))
			{
				int radius=(int)property.get("radius");
				double areaCircle=(3.142)*(radius*radius);
				result.put(String.valueOf(element), String.valueOf(areaCircle));
			}
			else if(type.equalsIgnoreCase("square"))
			{
				int side=(int)property.get("side");
				long areaSquare=(side*side);
				result.put(String.valueOf(element), String.valueOf(areaSquare));				
			}
			element++;
		}
		response.setSuccessful(true);
		response.setErrorMessage(null);
		response.setResult(result);
		return response;
	}
}
