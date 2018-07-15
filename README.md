# Java_EE_Udemy22
Looking up Stateful EJBs through Java Naming and Direcectory Interface (JNDI)
This tutorial uses Context and Object to link FlightDetails to each EJB object.

try {
			
			Context context = new InitialContext();
			
			Object fsObject = context.lookup("java:global/ejb10/flightStateless!com.airline.service.FlightLocal_ejb10");
			this.fs = (FlightLocal_ejb10) fsObject;
			
			Object fsStatefulObject = context.lookup("java:global/ejb10/flightStateful!com.airline.service.FlightLocal_ejb10");
			this.fsStateful = (FlightLocal_ejb10) fsStatefulObject;
			
			
		}
		catch(NamingException e) {
			
			System.out.println("Naming exception has occured in the lookup of our FlightService EJBs");
			e.printStackTrace();
			
		}
		
		//Stateless
		
		out.println("Flight Details: " + fs.getFrom() + " to " + fs.getTo() + " costing " + fs.getPrice());
		

		//Stateful
		out.println("Flight Details: " + fsStateful.getFrom() + " to " + fsStateful.getTo() + " costing " + fsStateful.getPrice());
