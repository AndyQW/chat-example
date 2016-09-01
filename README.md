# chat-example

This single page chat application demonstrates how to use socket.io with angular 1.5 framework. This application has following features:

1. Angular 1.5 component-based application structure:

   UI is wraped into a component: chat-window, which includes view (/chat-window.html) and controller implementation.

2. Event-based bi-directional communication layer with socket.io

   Socket.io is a realtime library, which provieds emit() function to send message to server, and on() function to listen message from server.

   Notice that we wrap socket.on callback in $rootScope.$apply. This tells AngularJS that it needs to check the state of the application and update the templates if there was a change after running the callback passed to it, so that Angular can update the view chat-window accordingly.


3. Store business data and logic in service
   
   The service Messager provide a public method GetMessages to exposure the internal object: _messages, so the model $ctrl.messages in controller of chat-window use _messages as data store. When socket receives message, and push the message to data store _messages, the model $ctrl.messages in chat-window will be updated automaticaly.
   
   This feature helps to create a loose-coupled application, and the component and service could be reused in different applications.

## Installation

1. git clone the responsitory
2. cd chat-example
3. npm install
4. npm start


## Test the application

1. Open multiple browser tabs and connect to localhost:3000; 
2. Input a message in any chat window and click button *Send; (Empty message will be ignored.)
3. All clients will receive the message.