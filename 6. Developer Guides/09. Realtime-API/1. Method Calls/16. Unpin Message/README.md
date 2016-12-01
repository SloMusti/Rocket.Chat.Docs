# Unpin Message
Unpinning a message allows administrators and owners of rooms to remove pinned items from being pinnned after they are no longer valid, [click here for more information on pinning messages][1].

## Requirements
| Logged In | Permission | Setting |
| --- | --- | --- |
| Yes | _none_ | `Message_AllowPinning` - "Allow Message Pinning" |

## Example Call
The only parameter that needs to be passed in is the [Message Object][1] and as of release `0.46` you need to send the entire message object otherwise an internal error will happen ([fixed via pull request #5087](https://github.com/RocketChat/Rocket.Chat/pull/5087)).
```json
{
    "msg": "method",
    "method": "unpinMessage",
    "id": "20",
    "params": [ fullMessageObject ]
} 
```

## Example Response
The response of a message being pinned is a new chat message which contains the broadcast of the message pinning. See [Message Object Details][1] for information about the response format.
```json
{
    "msg": "result",
    "id": "20",
    "result": {
        "t": "message_pinned",
        "rid": "QFtTnPJ4XbG634Skm",
        "ts": { "$date": 1480613343046 },
        "msg": "",
        "u": {
            "_id": "gHwBwDomPrCoQj7i2",
            "username": "bradley"
        },
        "groupable": false,
        "attachments": [{
            "text": "test",
            "author_name": "bradley",
            "author_icon": "/avatar/bradley.jpg?_dc=0",
            "ts": { "$date": 1480613302330 }
        }],
        "_updatedAt": { "$date": 1480613343046 },
        "_id": "sBYLyaHFkMdr7LKGt"
    }
}
```

```json
{"msg":"method","method":"unpinMessage","params":[{"rid":"QFtTnPJ4XbG634Skm","msg":"blah","ts":{"$date":1480615028589},"u":{"_id":"gHwBwDomPrCoQj7i2","username":"bradley"},"_updatedAt":{"$date":1480615033504},"pinned":false,"pinnedAt":{"$date":1480615033504},"pinnedBy":{"_id":"gHwBwDomPrCoQj7i2","username":"bradley"},"roles":["admin",null],"_id":"XudJNvnPEajGhhbHB","html":"blah","tokens":[]}],"id":"12"}
```

[1]:../../../4.%20User%20Guides/Pinning%20Messages