Podcast recording app.
The concept here is to be able to send a guest
a link and intervew them using their Android or IoS Phone

NOTE - This is ALPHA quality software, it may break, lose your recordings, frighten your cat etc...

This is based on the observation that most smartphones have decent microphones and a reasonable echo canceller,
so we can get pretty good recordings from them, certainly better than the corresponding laptops.

We don't want the guest to have to do anything difficult, the aim is to make this like talking on the phone, just higher quality.

The recording is only done on the host's side,
and is mixed so that they are on the left and the interviewee
is on the right,

All done with webaudio - no server needed - except
|pipe|'s rendezvous server.

Based on some work I did for family systems, but with their
special source removed!


How to use it.

Host: I use a laptop with headphones and a decent external Mic, but you can just use an Android phone.
In Chrome (Android or laptop only - IoS comming soon) browse to https://pipe.github.io/podcall/ 
this creates a link, share it with your guest somehow (I screenshot the QR and email it).
Click 'Done' - and wait for the guest to join. (you must click 'Done' before the guest 'Accepts')
DON'T CLOSE THE BROWSER TAB - the recording isn't saved untill you end the call, so you'll lose audio if
you just nuke the tab!

At the end of the call click the square button, then WAIT a few seconds until you see that the audio has been sucessfully saved. 
The saved audio is an ogg/opus file - this is smaller than the original version which used WAV - but since the conversation was
conducted in opus it should not be lower quality. Audacity can convert back to WAV if needed.

Guest: When you get the invite - open it in chrome on Android or safari on IoS11. Click 'Accept' and agree to the dropdown to 
asking to allow the page to access your microphone (first time only), place the phone somewhere comfortable, adjust the speaker volume and just talk. (The mic symbol mutes/unmutes your microphone, the square ends the call). 

Enjoy! Please file issues or PRs with patches!
Tim.


