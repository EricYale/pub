# Session Fixation Attack
Presume there's an application that does a bad job of keeping track of session IDs.

1. Attacker makes a request to the server and gets a session ID
2. Attacker tricks the victim into using that session ID
3. Victim elevated the session ID, i.e. by logging in
4. Attacker can now use the session ID to access the victim's account

To prevent this, the server should send a new session ID whenever authentication state changes/
