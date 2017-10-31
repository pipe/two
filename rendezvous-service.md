Rendezvous server for unrupt.

Unrupt uses WebRTC to connect the audio of 2 web browsers (typically safari).

To set up a WebRTC 'call' requires that browser A creates an opaque blob of data called an 'offer', which is sent to browser B
browser which creates a complimentary blob called an 'answer' which is then sent to Browser A. Exchanging this 'offer/answer'
is (almost) sufficient for the two browsers to be able to create a direct connection between them.

(*) - almost because there are some other (smaller) blobs exchanged (called candidates) which decribe the available
network interfaces on a webRTC capable browser.

We do this exchange over websockets to a central web service that is known to both parties.

The web service needs to do the following:

1) accept websocket connections
2) associate the websocket connection with an ID as a url param
3) recieve messages (in json) over websocket(s)
4) (optionally) check that a 'from' field exists in the message and that it matches the source websocket's id
5) inspect the 'to' field in a received json message
6) determine if any current websockets have an ID that match the 'to' field
7) send the message out on the matching websocket

a nice feature would be to reject websocket connections where the id is already taken.

An implementation in scala can be found here: https://github.com/steely-glint/fingersmith

Here's how unrupt uses this service:

            var mid = getMyId();
            var socket = new WebSocket( "wss://pi.pe/websocket/?finger=" + mid);
            socket.onmessage = (event) => {
                    var data = JSON.parse(event.data);
                    if (data.to != mid){
                        alert("message mixup");
                    }
                    switch (data.type) {
                        case "offer":
                            // setOffer
                            break;
                        case "answer":
                            // setAnswer
                            break;
                        case "candidate":
                            // etc
                    }
                }
            
                function sendMessage(to,from,type,data){
                    var messageJ = {to:to,from:from,type:type,sdp:data};
                    var message = JSON.stringify(messageJ);
                    console.log("sending "+message);
                    socket.send(message);
                }