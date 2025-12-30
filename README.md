First - I run docker-compose.yml in order to have postgres and RabbitMQ docker containers.
I've been created 3 projects, EventsApi, EventConsumer, BL
    EventsApi - an WebAPI which expose Get (GarageOccupancy counters from table "GarageOccupancy")and POST (insert new events)	
    EventConsumer - which listen to RabbitMQ queue, calculate the occupancy and store the results in the  GarageOccupancy table , but only after the "ENTRY" and "EXIT" events.
    BL - which is common to both above and handle the logic and the Accessors to postgres
EventId,OccurredAtUtc,  will populated by EventAccessor (when Insert...).
when we count - we ignore the rows with 'PAY' status.

