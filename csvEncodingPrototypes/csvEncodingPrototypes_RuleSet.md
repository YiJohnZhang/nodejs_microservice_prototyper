# Rule Set
- CSV File:
	- is tab,`\t`, delimited and text is enclosed in double quotes.
	- is named: `fileName.csv` where `fileName` = `projectName_levelInt_componentName` 
- Any `Identifier` fields are parsed as strings; they must follow the following naming rules:
	- The name can contain A – Z, a – z, 0 - 9, underscore; must start with a letter or an underscore.
- Any `Name` fields are parsed as strings.
- Any `Description` fields are parsed as strings.
	- It is **GOOD PRACTICE** that it should be < 150 characters (~30 words) but ideally < 100 characters (~20 words) including punctuation.
- Any `Subtitle` fields are parsed as strings.
	- It is **GOOD PRACTICE** that it should be < 30 characters (abbreviations only) if they exist.
- The `Type` field is an enumeration of the possible following strings:
	- C1, Context Diagram: Person, System of Interest, System
	- C2: Container Diagram: Person, Component, Database Component, Browser Component, Mobile Component, External System / Component 
	- C3: Component Diagram: Person, Component, Database Component, Browser Component, Mobile Component, External System / Component
	- C4: UML Diagram
- Reserved Words
	- **Table Headings**: [`Blocks`, `Matrix`, `Edge Mapping`, `UML Table`], Table Headings double as section breaks.
		- `Blocks`, `Matrix`, and `Edge Mapping` should be used for levels 1 - 3 of the C4 Model (Context, Container, Component).
		- `UML Table` exists on level 4 (Code) of the C4 model, it should be exist in a document mutally exclusive to `Blocks`, `Matrix`, and `Edge Mapping`; therefore, ++==***reserving `UML Table` is redudndant?***==++
	- `end`
		- consider it to be used to denote the end of a table.
		- likely redundant because of **Table Headings**
	- `Source File`
		- the source file to **eventually** directly edit if the documentation updates
	- ++==***`Documentation File`?***==++
		- the documentation file to **eventually** directly edit if the documentation updates
		
# Intended Usage
0. High-Level Diagrams
	- `Blocks` Table
		- Identifier (`string`): A unique identifer for the corresponding `Name`, `Type`, and `Description`.
		- Name (`string`): Display Name in the diagram.
		- Type (`enum`, `string`): Determines the icon to display / its corresponding color-coding.
		- Description (`string`): 
	- `Matrix` Table
		- Identifier (`string`): The unique identifer for the corresponding `Name`, `Type`, and `Description` from `Blocks`.
		- x (`Number`): haven't quite figured out if this is to be relative _-coordinate; reserved for future GUI display information.
		- y (`Number`): haven't quite figured out if this is to be relative _-coordinate; reserved for future GUI display information.
		- ...Identifer: All *n* identifiers displayed.
		- Consider using a `List` => and store "anchor" as a data point.
	- `Edge Mapping` Table
		- Identifier (`int`): in the matrix, the integers do not represent weight: they represent the edge identifier that holds the appropriate description for the relationship
		- Description (`string`): Usually a verbal phrase describing the relationship.
		- Subtitle (`string`): Usually the communication protocol / object used.
		- startAnchor (`int`): Each block will have 8 anchors (N, ..., W, NE, NW, ...); this is to help the app draw the appropriate lines. Probably wil increase it later on.
		- endAnchor (`int`): Each block will have 8 anchors (N, ..., W, NE, NW, ...); this is to help the app draw the appropriate lines. Probably wil increase it later on.
1. Context Diagram: 
	- See **0. High-Level Diagrams** with any conflicts overwritten below.
	- For navigation and system uptime UI.
2. Container Diagram
	- See **0. High-Level Diagrams** with any conflicts overwritten below.
	- For navigation and system uptime UI.
3. Component Diagram
	- See **0. High-Level Diagrams** with any conflicts overwritten below.
	- For design / navigation and system development UI.
4. Code
	- This is intended to generate documentation for TDD (*failed TDD attempts flashbacks: []() and []()*).
	- For now `Class` is assumed to be a module.

Darn, it has been 1.5 hours since I last edited this section and forgot what else to add ._.

++==Eventually: A built-in text interface that allows modifying L3 (module documentation) and L4 (method documentation and master documentation) can edit the code files in real-time. I'm guessing this could be found by looking for the method signature and modifying the multi-line comment directly above it until empty space/code line breakers.==++