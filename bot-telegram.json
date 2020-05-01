[
    {
        "id": "be56b61c.628bd8",
        "type": "tab",
        "label": "Flow 2",
        "disabled": false,
        "info": ""
    },
    {
        "id": "666ce158.1f6d48",
        "type": "watson-conversation-v1",
        "z": "be56b61c.628bd8",
        "name": "",
        "workspaceid": "25761b97-2cc5-4342-9136-36779fb08280",
        "multiuser": false,
        "context": false,
        "empty-payload": true,
        "default-endpoint": true,
        "service-endpoint": "https://gateway.watsonplatform.net/assistant/api",
        "timeout": "",
        "optout-learning": false,
        "x": 622,
        "y": 192,
        "wires": [
            [
                "ca68b236.e74fb"
            ]
        ]
    },
    {
        "id": "4ab10dc9.f4e63c",
        "type": "function",
        "z": "be56b61c.628bd8",
        "name": "Text_to_Telegram",
        "func": "msg.payload = {\n    chatId: msg.chatId,\n    type: \"message\",\n    content: msg.payload.output.generic[0].text\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1113,
        "y": 102,
        "wires": [
            [
                "83dc692a.45e18"
            ]
        ]
    },
    {
        "id": "83dc692a.45e18",
        "type": "telegram sender",
        "z": "be56b61c.628bd8",
        "name": "",
        "bot": "39d8988f.2b0eb8",
        "x": 1429,
        "y": 200,
        "wires": [
            []
        ]
    },
    {
        "id": "f87d5d70.07e888",
        "type": "telegram receiver",
        "z": "be56b61c.628bd8",
        "name": "",
        "bot": "39d8988f.2b0eb8",
        "saveDataDir": "",
        "x": 122.49998474121094,
        "y": 196.20001220703125,
        "wires": [
            [
                "dbe065b8.0135e",
                "2bdadbb7.bb8cec"
            ],
            []
        ]
    },
    {
        "id": "dbe065b8.0135e",
        "type": "function",
        "z": "be56b61c.628bd8",
        "name": "Telegram_to_Watson",
        "func": "msg.chatId = msg.payload.chatId;\nmsg.payload=msg.payload.content;\n\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 379.5,
        "y": 194.5999755859375,
        "wires": [
            [
                "666ce158.1f6d48"
            ]
        ]
    },
    {
        "id": "ca68b236.e74fb",
        "type": "switch",
        "z": "be56b61c.628bd8",
        "name": "Que tipo de respuesta es?",
        "property": "payload.output.generic[0].response_type",
        "propertyType": "msg",
        "rules": [
            {
                "t": "eq",
                "v": "text",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "image",
                "vt": "str"
            },
            {
                "t": "eq",
                "v": "option",
                "vt": "str"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 3,
        "x": 843,
        "y": 194,
        "wires": [
            [
                "4ab10dc9.f4e63c"
            ],
            [
                "1b8e83b3.20a554"
            ],
            [
                "a8a62099.fa1258"
            ]
        ]
    },
    {
        "id": "1b8e83b3.20a554",
        "type": "function",
        "z": "be56b61c.628bd8",
        "name": "Images_to_Telegram",
        "func": "msg.payload = {\n    chatId: msg.chatId,\n    type: \"message\",\n    content: msg.payload.output.generic[0].source\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1112,
        "y": 196,
        "wires": [
            [
                "83dc692a.45e18"
            ]
        ]
    },
    {
        "id": "a8a62099.fa1258",
        "type": "function",
        "z": "be56b61c.628bd8",
        "name": "Options_to_Telegram",
        "func": "msg.payload= {\n    chatId:msg.chatId, //indentificación del usuario\n    content : msg.payload.output.generic[0].title, //título del mensaje\n    type:\"message\", \n    options:{ \n        reply_to_message_id:msg.messageId,\n        reply_markup:{\n        keyboard:[\n            [{text: msg.payload.output.generic[0].options[0].label}], //opción 1\n            [{text:msg.payload.output.generic[0].options[1].label}] //opción 2\n        ],\n        'resize_keyboard': true,\n        'one_time_keyboard': true\n        \n    }},\n};\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 1120,
        "y": 277,
        "wires": [
            [
                "83dc692a.45e18"
            ]
        ]
    },
    {
        "id": "2bdadbb7.bb8cec",
        "type": "debug",
        "z": "be56b61c.628bd8",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "false",
        "x": 347,
        "y": 265,
        "wires": []
    },
    {
        "id": "39d8988f.2b0eb8",
        "type": "telegram bot",
        "z": "",
        "botname": "Paiepbot",
        "usernames": "",
        "chatids": "",
        "baseapiurl": "",
        "updatemode": "polling",
        "pollinterval": "300",
        "usesocks": false,
        "sockshost": "",
        "socksport": "6667",
        "socksusername": "anonymous",
        "sockspassword": "",
        "bothost": "",
        "localbotport": "8443",
        "publicbotport": "8443",
        "privatekey": "",
        "certificate": "",
        "useselfsignedcertificate": false,
        "verboselogging": false
    }
]
