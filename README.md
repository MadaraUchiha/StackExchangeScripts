##SEChatModifications
Provides keyboard shortcuts and other commands via input text reducing 
the dependency on mouse usage.  Currently the script adds the id to the 
right of each message and the commands take in this id to identify the 
selected message. Keyboard navigation support has also been added allowing 
for individual messages to be navigatable through the keyboard.

### Performing an action on a message

All of the following commands take a single arugement - the id of the 
message you want the action to be performed. You can find the id on the 
right side of each message beside the timestamp

* `/star` - star the message 
* `/del` - deletes the message
* `/edit` - edits the message
* `/quote` - quote the message whose id you pass, by posting a link to it
* `/flag` - will flag the message as offensive, spam or noise
* `/history` - displays the edit history of that message
* `/jump` - scrolls to that message if it is 

`/edit` and `/delete` can only be performed during the two minute grace 
period, after which the message is locked. The message id can be left 
out for these two commands to perform the action on your last message. 

### Room commands

* `/load` - loads more messages
* `/list <filter>` - list all rooms, ordered by activity. Rooms will be 
  filtered by `<filter>` if it is provided
* `/join <id>` - join the room with the `<id>`. Usually used in 
  conjunction with `/list`
* `/switch <match>` - switch to a room which you have already joined. 
  Takes a (partial) substring of the room name you are switching to
* `/transcript <search>` - view the room transcript. Performs a transcript 
  search if `<search>` is provided
* `/leave <match>` - leaves the room with name or id matching `<match>`, 
  or all rooms if `all` is used, or the current room if nothing is passed

### User commands

* `/last <username>` - scrolls to the last message said by the user. `<username>` 
  can be a partial match
* `/profile <site> <name>` - searches the `<site>` for users with display name 
  matching `<name>`. `<site>` will go through common abbreviations like MSO, AU 
  and 8bitlavapwnpwniesbossstagesixforhelp before defaulting to `<site>.stackexchange.com`
* `/me <message>` - wraps the `<message>` in a pair of `*` to italicise it in a 
  lame attempt at emulating IRC `/me`

### Pseudo-Oneboxes

The `/ob [url]` command will create onebox-like series of messages that attempt 
to add onebox support for sites not "officially supported". The following sites 
are currently supported:

* **Vimeo:** Video links will be turned into a preview frame 
  image of the video plus a link to the video in question. 
  *Only the link, not the image, will take you to the video.*
  
  Supported URL formats:
  * `http://vimeo.com/{video-id}`
  * `http://vimeo.com/channels/{channel-name}#{video-id}`
  * `htt[://vimeo.com/category/{group-name}/videos/{video-id}`

### Highlighting messages

In high volume rooms messages or conversations can often be lost under the 
deluge of activity. Highlighting messages can be a useful way of keeping 
a temporary bookmark or keeping track of one or more user's messages. 

The `/hl <match>` command takes a message id or a username match to highlight 
that particular message or user's messages. Calling it without any arguments 
will list all active highlight rules. 

### Clipboard

The clipboard is a place to store messages and notes to yourself.

* `/jot [match]` is used to take down messages or notes.
	* If `[match]` is a number, than the message with that id is taken 
	  down into the clipboard, else everything else after `/jot` is 
	  stored into the clipboard as a note.
	* After jotting down things into the clipboard, an id will be shown.
	  This id will be used to refer to the note when pasting or 
	  removing the message from the clipboard.
* `/clips` will show a list of all messages and notes taken. Clips and also be managed from here.
* `/paste [id]` if a message is pasted, that message will be **quoted**, 
  else a new message with the note's content will be generated
* `/rmclip [id]` will remove the clip with that id from the clipboard
    
### Keyboard Navigation

  * `Ctrl` + `Up Arrow` begins navigation
  * `Ctrl` + `Down Arrow` cancels navigation and jumps to message input
  * `Up Arrow` and `Down Arrow` navigate between messages
    * `Page Up` and `Page Down` navigate more quickly (5 messages at a time)
  * On a selected message:
    * `Q` quotes the selected message
    * `E` edits the selected message
    * `R` begins a reply to the selected message
    * `D` removes the selected message
    * `S` stars the selected message
    * `H` shows the history of the message
    * `F` puts the command to flag a message in the input box
    * `J` jumps to the replied-to message, if the selected message is 
      an explicit reply
    * `Right Arrow` edits or begins a reply to the selected message, 
      depending on if you own it
    * `Left Arrow` and `P` display the replied-to message, if the 
      selected message is an explicit reply

### Other features

The script will add the id of every message as well as its timestamp on 
the right of every message, to aid in using some of the commands. Rate 
limited messages can be retried with `ctrl` + `space`

## SEModifications
Provides minor tweaks to StackExchange sites.

* Adds a timeline link to each question page
* Turns comment timestamps into links to the comment
  * Will only work if the comment is visible when the page is linked 
    to (Unless you have this script).
* Adds audit link to /reputation
* Adds history link to each question and answer

### Autocomplete

![Comment reply autocomplete in action](http://i.imgur.com/eTq50.png)

This script also adds chat-like autocomplete for comments replies, in a way (relatively) 
consistent with [these criteria](http://meta.stackoverflow.com/questions/43019/how-do-comment-replies-work/43020#43020). 
Note that while editors can be notified, their usernames will not show up 
on the list of names. 

##SEChatFaviconNotifier

![Chatroom favicons with different numbers of unread message counts](http://i.imgur.com/llq97.png)

Adds unread count and @-mention notifications directly to the favicon of 
the chatroom page. The circle shows the number of unread messages and 
turns green when someone @-mentions you.
