{
	// Place your snippets for javascript here. Each snippet is defined under a snippet name and has a prefix, body and 
	// description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
	// $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the 
	// same IDs are connected.

	//helpful general logging
	"Print to console": {
		"prefix": "clg",
		"body": [
			"console.log($0);"
		],
		"description": "Log output to console"
	},
	//helpful for react dev
	"arrow function": {
		"prefix": "function",
		"body": [
			"const $1 = ($2) => {",
			"	$3 ",
			"}$0"
		],
		"description": "Create arrow function"
	},
	//helpful for react dev
	"function with default export": {
		"prefix": "function",
		"body": [
			"const $1 = ($2) => {",
			"	$3 ",
			"}",
			"",
			"export default $0;"
		],
		"description": "Create a function with default export"
	},
}
