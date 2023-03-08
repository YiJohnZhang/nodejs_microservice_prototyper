# nodejs_microservice_prototyper
A web application to prototype a web application built with the microservice architecture. Theoretically, it may also be used for an application built with monolith architecture as well, however, I do not have intention to develop a means to automatically integrate it into one.

# idea dump (to organize)

## automating high-level parts of a web application:
C4: Context, Container, Component, Code
1. **System Context Diagram**. A very high-level overview. It consists of the end-user and the system. Plain language that names the system, entity type, and a *brief* description of each system. Interactions between system(s) are equally brief and representative of a graph ds. Typically the system of interest is colored and all other(s) grayed out.
	- Software System (of Interest);
	- External System (Container);
	- User;
	- Relationship (allow 2-way relationships)
2. **Container Diagram**. A focused overview of the system of interest where it is decomposed into "applications" and how they interact with external system(s) including the communication protocol used. The brief description of each container focuses on its high-level, i.e. "Single-Page Web Application: provides all functions to the user in a web browser", "Mobile App: provides a limited subset of internet functions to the user over their mobile device", "Database: Only stores information related to user credentials, access logs, etc.", "API Application: Exposed access point for all of application functionality.".
	- Container; Container, Database; Container, Mobile; Container, Browser;
	- External System (Container);
	- User;
	- Relationship (be able to make two arrows, detailing what it sends and what it expects in return) w/ protocol 
3. **Component Diagram**. Expands on a "Container" of interest into its components. I'm guessing this is a lot like the "models" that are relevant for this API. Some jargon: ["Controller": Components that "dispatch?" actions to Components that are implemented to do whatever aspect?, "Facade": A Component to...? I'm guessing this is a transciever Component for the Container?](https://c4model.com/)
4. **Code**. UML reigns supreme here.

There needs to be "C5": Consumer (End-User), Context, Container, Component, Code. Because an application may have an adminstrator, [various business-level internal "consumers"], and "generic external consumer". the idea is that ideally, each "consumer" gets a separate interface that only gets read/write as much data for them from a central database?
- better add an orthogonal "Class (Abstract Class)" => 6C?

Motivation for this:
- flashbacks of that disastrous attempt at TDD
- supreme laziness.
- make a software engie capable of designing a web app w/ a spreadsheet sounds pretty cool + they could handle the code => a software engie can design both the whole software system.

implementaiotn ideas:
- adjacency matrix, 0 => no rel (no self rel) & int for edge to map to a text description.
- use a "BREAK" to break betwen the table and edge
- i want to maybe generate a json or w/e so it can be dumped into react for interactivity.
	- add "coordinates" so that a react app can generate a setting

## automating low-level development
The idea is a library that takes JSON input to:
- build the database seed
- build the corresponding query group(s)
- compatible with low-level pre-implemented query builder (extendable so that users can build business-logic query.)

i.e.
```js
modelName
properties[
	{
		propertyName
			// expect string type
		type:
			// array = [], enum = [...], stringifiedObject = {}, string, numberInteger (smallint, int, bigint, smallserial, serial, bigserial), numberFloat (), date, string (varchar(x), text(x), varchar, text)
		defaultValue
			// expect to be of propertyName type; default undefined
		primaryKey:
			// boolean
		foreignModel
			// boolean
		nullable
			// boolean; default true
		unique
			// boolean; default false
		acid
			// boolean; default false; description: cascade on update/delete
		class: []
			// array; the group this property belongs to
	}
]
```
automating low-level parts of a web application:
- maybe start with a documentation generator (csv => md)
- then expand to a csv parser used to generate relations
- expand to a csv parser used to generate a psql seed file
	- w/ comments
	- consider a gui-text hybrid (i.e. quickdbdiagrams) platform that accepts csv / can generate it.
- expand to a csv parser 

Other ideas:
- a port of flask-wtform that is compatible with React 18+ and bootstrap
