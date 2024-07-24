part 0: Fundamentals of Web apps
----------------------------------
    -Notes:
        - Always keep the Developer Console open on your web browser.
        - On Windows or Linux, open the console by pressing Fn-F12 or ctrl-shift-i
        - HTTP:
            - HTTP is am application layer for transmitting hyper media docs.
            - HTTP is designed for communication between browser & server
            - HTTP follow Client-Server Model
            - Client-Server Model: it is a request made by client and the server
                                processes the request amd sends a response
            - HTTP is a stateless protocol
            - servers doesn't keep any data between two requests
        - DOM: is an Application Programming Interface (API) that enables programmatic 
               modification of the element trees corresponding to web pages.
        - You can access the document object by typing document into the Console tab.

----------------------------------

application logic in browser:
----------------------------------
    -logic of page: https://studies.cs.helsinki.fi/exampleapp/notes

        var xhttp = new XMLHttpRequest()

        xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
            const data = JSON.parse(this.responseText)
            console.log(data)

            var ul = document.createElement('ul')
            ul.setAttribute('class', 'notes')

            data.forEach(function(note) {
            var li = document.createElement('li')

            ul.appendChild(li)
            li.appendChild(document.createTextNode(note.content))
            })

            document.getElementById('notes').appendChild(ul)
        }
        }
        
        xhttp.open('GET', '/data.json', true)   
        xhttp.send()

    - data.json contains the data of the website
    - line 42 -> 43: makes an HTTP GET request to server address /data.json
    - line 25 -> 38: - forms a bullet-point list from the note contents
                     - line 28 -> The code first creates an unordered list with a ul-tag
                     - line 31 -> 36: adds one li-tag for each note.
    - line 25 -> 26: makes an output in the console tab due to console.log
    - line 21 & 23 & 42 & 43: Event handlers and Callback functions 
    - line 23: event handler for the event onreadystatechange is defined for the xhttp object doing the request.
    - line 24: the state of the object changes, the browser calls the event handler function. The function code checks that the readyState equals 4 
               (which depicts the situation The operation is complete) and that the HTTP status code of the response is 200.
    - line 30 -> 37:  creates a new node to the variable ul, and adds some child nodes to it.
    - line 40: document.getElementById('notes').appendChild(ul)

----------------------------------

Manipulating the document object from console:
----------------------------------
    - The topmost node of the DOM tree of an HTML document is called the document object.
    - You can access the document object by typing document into the Console tab.
    - add a new note to the page from the console:
        1- we'll get the list of notes from the page. The list is in the first ul-element of the page:
            list = document.getElementsByTagName('ul')[0]
        2- Then create a new li-element and add some text content to it:
            newElement = document.createElement('li')
            newElement.textContent = 'Page manipulation from console is easy'
        3- add the new li-element to the list:
            list.appendChild(newElement)