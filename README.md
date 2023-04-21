

1. Drop and create the database:

    Drops the "property_website" database if it exists, creates it if it doesn't, and sets it as the current database. This ensures a clean state for the database before defining tables and procedures.

2. Create sellers table:

    Creates a table for sellers with columns for seller_id (auto-increment primary key), first_name, last_name, email, and phone_number. The table stores information about property sellers.

3. Create buyers table:

    Creates a table for buyers with columns for buyer_id (auto-increment primary key), first_name, last_name, email, and phone_number. The table stores information about property buyers.

4. Create properties table:

    Creates a table for properties with columns for property_id (auto-increment primary key), address, postcode, num_bedrooms, num_bathrooms, has_garden, property_type, price, status, and seller_id. Includes a foreign key constraint for seller_id, referencing the sellers table, ensuring a property cannot be added without an existing seller.

5. Create agents table:

    Creates a table for agents with columns for agent_id (auto-increment primary key), first_name, last_name, email, and phone_number. The table stores information about property agents.
    
6. Create bookings table:

    Creates a table for bookings with columns for booking_id (auto-increment primary key), property_id, buyer_id, start_date, end_date, and agent_id. Includes foreign key constraints for property_id, buyer_id, and agent_id, referencing the properties, buyers, and agents tables respectively.

7. Add property procedure:

    Adds a new property to the properties table if it doesn't already exist, based on address and postcode. Takes parameters for address, postcode, number of bedrooms, number of bathrooms, garden presence, property type, price, and seller_id. It checks if a property with the same address and postcode exists before inserting a new property. Note that the seller_id is required, so a seller must be added first before adding a property.

8. Search properties procedure:

    Searches for properties based on various filters including address, postcode, property_type, minimum and maximum price, minimum number of bedrooms, and minimum number of bathrooms. The procedure returns all properties that match the given criteria and have a status of 'FORSALE'.

9. Add seller procedure:

    Adds a new seller to the sellers table if the seller doesn't already exist, based on first_name, last_name, and email. Takes parameters for first_name, last_name, email, and phone_number. It checks if a seller with the same name and email exists before inserting a new seller.

10. Add buyer procedure:

    Adds a new buyer to the buyers table if the buyer doesn't already exist, based on first_name, last_name, and email. Takes parameters for first_name, last_name, email, and phone_number. It checks if a buyer with the same name and email exists before inserting a new buyer.

11. Withdraw property procedure:

    Withdraws a property from the properties table by setting its status to 'WITHDRAWN' if the current status is 'FORSALE'. Takes a property_id as a parameter. Raises an error if the property is already sold.

12. Resubmit property procedure:

    Resubmits a withdrawn property to the properties table by setting its status back to 'FORSALE' if the current status is 'WITHDRAWN'. Takes a property_id as a parameter. Raises an error if the property is not in the 'WITHDRAWN' status.

13. Update property procedure:

    Updates an existing property's details in the properties table using the provided information. Takes parameters for property_id, address, postcode, number of bedrooms, number of bathrooms, garden presence, property type, and price. The procedure updates only the provided fields, leaving the others unchanged.

14. Create booking procedure:

    Creates a new booking in the bookings table if the property is not sold, the agent is not busy during the specified time, and the property is not already booked during that time. Takes parameters for property_id, buyer_id, start_date, end_date, and agent_id. If any of the conditions are not met, an appropriate error message is raised.
