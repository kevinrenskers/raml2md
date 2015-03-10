# Example API documentation version 1
http://example.com/1

### Welcome
Welcome to the Example Documentation. The Example API allows you
to do stuff. See also [example.com](https://www.example.com).

```javascript
var raml2html = require('raml2html');

// Using the default templates:
// source can either be a filename, file contents (string) or parsed RAML object
raml2html.parse(source, onSuccess, onError);

// Using your own templates:
// - config should be an object with at least an `template` property
// - config can also include `helpers` and `partials`
// - the config object will be accessible from your handlebars templates
raml2html.parseWithConfig(source, config, onSuccess, onError);
```

### Chapter two
More content here. Including **bold** text!

---

## ACCOUNTS
This is the top level description for /account.
* One
* Two
* Three

### /account

* **post**: Creates a new account. Some **bold** text here. More text. Need to fill the line, so make it longer still. Hooray!
    Line two
    
    Paragraph two
    
    * **Responses**:
        * *200*: Account was created and user is now logged in

### /account/find

* **get**: find an account
    * **Query parameters**:
        * `name`:name on account
            * name: name
            * type: string
            * default: none
            * *required*
            * example: Naruto Uzumaki
        * `gender`:
            * name: gender
            * type: string
            * default: none
            * *required*
        * `number`:
            * name: number
            * type: integer
            * default: 42

### /account/{id}

* **get**: 

* **put**: Update the account

* **delete**: Delete the account

### /account/login

* **post**: Login with email and password
    * **Responses**:
        * *200*: Login was correct
            * body:
                * text/xml:
                    * example:

                            <test>This is a test</test>
                            
        * *400*: Login was incorrect, please try again

        * *401*: Not authorized

### /account/forgot

* **post**: Sends an email to the user with a link to set a new password

### /account/session

* **get**: Gets the sessions

* **delete**: Deletes the session, logging out the user

## Forecasts
The very top resource - displays OK

### /forecasts/{geoposition}
Overview endpoint to assemble and access forecast data in various timely resolutions - THIS IS NOT DISPLAYED ANYWHERE WITH RAML2HTML :/

* **get**: Provides an overview of the available data - display OK

### /forecasts/test
No methods here, but it does have a description

## /conversations
This is the top level description for /conversations.

### /conversations

* **get** *(secured)*: Get a list of conversation for the current user

* **post** *(secured)*: Create a new conversions. The currently logged in user doesn't need to be supplied in the members list, it's implied.
    * **Responses**:
        * *200*: A conversation with these members already existed, the message was added to that one

        * *201*: The conversation was created and the message added to it

### /conversations/{convId}

* **get**: Get a single conversation including its messages

* **put**: Update a conversation (change members)

### /conversations/{convId}/messages

* **get**: Get the messages for the conversation
    * **Query parameters**:
        * `page_size`:The number of items per page
            * name: page_size
            * type: number
            * default: 20
        * `page`:The page to return
            * name: page
            * type: number
            * default: none

* **post**: Add a new message to a conversation

### /conversations/{convId}/messages/{messageId}

* **put**: Update the message

* **delete**: Delete the message

## /users

### /users

* **get**: Get a list of all users
    * **Query parameters**:
        * `page_size`:The number of items per page
            * name: page_size
            * type: number
            * default: 20
        * `page`:The page to return
            * name: page
            * type: number
            * default: none

* **post**: Creates a new user

### /users/{userId}

* **get**: Get the details of a user including a list of groups he belongs to

* **put**: Update a user

* **delete**: Deletes a user

## /groups

### /groups

* **get**: Get a list of all the groups

* **post**: Create a new group

### /groups/{groupId}

* **get**: Get the details of a group, including the member list

* **put**: Update the group, **optionally** supplying the new list of members (overwrites current list)

* **delete**: Removes the group

### /groups/{groupId}/users

* **post**: Adds a user to a group

### /groups/{groupId}/users/{userId}

* **delete**: Removes a user from a group

