![alt text](https://github.com/devmohamedsamir/tourism-company/blob/main/reserve-room-hotel.png)
![alt text](https://github.com/devmohamedsamir/tourism-company/blob/main/reserve-ticket-flight.png)
![alt text](https://github.com/devmohamedsamir/tourism-company/blob/main/tourism_agency.drawio%20(1).png)
![alt text](https://github.com/devmohamedsamir/tourism-company/blob/main/add-supplier.png)
![alt text](https://github.com/devmohamedsamir/tourism-company/blob/main/flights.png)
![alt text](https://github.com/devmohamedsamir/tourism-company/blob/main/hotels.png)
![alt text](https://github.com/devmohamedsamir/tourism-agency/blob/main/tourism_agency.drawio%20(1).png)
Tourism system: [scenario]
	can give customers 3 services for reservations from 3 suppliers  
	services of reservations  
		first service we have flights 
		second service we have cars
		third service we have hotels
    
	suppliers that our agency can make reservation with
		first supplier flights companies data
		second supplier cars companies data 		
		third supplier cars companies data
    
***************
database tables 
***************
	contacts table represents [suppliers companies of(flights - cars - hotels) and customers and roles]
		id [pk]
		name [string]=>both
		phone [string]=>both
		email [string]=>both
		personal_id	 [integer - limited - nullable]=>customers
		vat_id [string - limited - nullable]=>suppliers
		coc [string - limited - nullable]=>suppliers
		contact_type [enum][supplier - customer] =>both
	
	services table represents [flights - cars - hotels]
		id [pk]
		service_name [enum][car - hotel - flight]
		service_description [string]=>all
		from_location [string] null=>[car - flight]
		to_location [string] null=>[car - flight]
		from_time [datetime] null=>[car - flight - hotel]
		to_time [datetime] null=>[car - flight - hotel]
		duration_service [integer] =>[car - flight - hotel]
		contact_id [fk][integer] =>both
		availablity_id [integer] =>all
		number_of_adults [integer null] =>hotels
		number_of_children [integer null]=>hotels
		room_type [enum null] =>hotels
		seat_numbers [integer null]=>flights
		trip_type [enum ]=>flights
		class_type [enum ] =>flights
		
	cars_models_brands table for 
		id [pk]
		model_name [string]
		brand [string]
		model_year [integer]
		service_id
		
	prices table for service money calculations
		id [pk]
		type_service [enum]=>[room - car_rental - ticket ]
		from_location [string] null=>[car - flight]
		to_location [string] null=>[car - flight]
		from_time [datetime] null=>all
		to_time [datetime] null=>all
		duration_service [integer] =>all
		price [float]=>all
		total [float]=>all
		service_id [fk][integer]=>all
	
	availability
		id [pk]
		from_time [datetime] =>all
		to_time [datetime]=>all
		available [boolean] =>all
		
	roles table for employees [admin -sales.....]
		id [pk]
		Role_name
	
	transactions table for knowing what is happing in payments 
		id [pk]
		from_date [datetime] =>all
secanrio 1 
	 => as a customer needs to reserve hotel room 
	 => call our system for it 
	 => our empolyee(sales) will response on it 
	 => customer will choose a hotel location and number of rooms beds and number of days 
 	 => customer will choose from form of data what is customer need 
	 => total price will shown 
	 => customer confirmation required 
	 => we need to get total price from him manually or credit
	 => 
senario 2
	=> as a customer needs to reserve plane ticket 
	=> call our system for it 
	=> our empolyee(sales) will response on it 
 	=> customer will choose [from where => to where] and time of his flight will be
 	=> numbers of seats and trip type and class type [2 ways or on way ]
 	=> total price will shown 
	=> customer confirmation required 
	=> we need to get total price from him manually or credit
