Audio should be sent using a separate UDP connection. 

There should be a UDP connection for sending audio and a UDP connection for recieving audio.

Servers should combine the audio of all incoming audio connections and send the combined audio to the outgoing connections.