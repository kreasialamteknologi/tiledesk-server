

# 2.1.17
- Log fix

# 2.1.16
- CSV export fix

# 2.1.15


- Automatically close unresponsive bot conversation  (also in 2.1.14.4). You may configure CLOSE_BOT_UNRESPONSIVE_REQUESTS_CRON_EXPRESSION, etc.
- Added _answerid field to the messages replies send from the chatbot under attributes field.
- Added fulltext indexes for request.notes request.tags and request.subject.. 
- Added default language field for pivoting. We disabled pre traslation for EN, IT, FR. So only pivot language is taken into account. Included database migration script:  1604082287722-labels-data-default-fields--autosync.js
- Added status field to project_user collection. Included database migration script: 1603797978971-project_users-status-field-added--autosync.js
- Added channel_type (group or direct) and channel (chat21, whatsapp, etc..) fields to the message model. Included database migration script: 1602847963299-message-channel_type-and-channel-fields-added--autosync.js
- Added posfix $reply_time to WAITING_TIME_FOUND label. Included database migration script: 1604082288723-labels-waiting_time-added_suffix_reply_time--autosync.js
- Added channelOutbound (chat21, whatsapp, etc..) fields to indentify the outboud channel to the request model. Included database migration script: 1603955232377-requests-channel-outbound-fields--autosync.js
- Renamed request field UNSERVED (100) to UNASSIGNED (100) and SERVED (200) to ASSIGNED (200)
- Renamed property max_agent_served_chat to max_agent_assigned_chat of the project.settings object.Included database migration script: project-settings-max_agent_assigned_renamed--autosync
- Renamed property max_served_chat to max_assigned_chat of the project_user object. Included database migration script: project_user-max_assigned_chat-renamed--autosync
- SourcePage and bot answer stats with tiledesk-ent/tiledesk-server-analytics: 1.1.9
- Fix Conversation export to CSV
- Bots statistics with tiledesk-ent/tiledesk-server-analytics: 1.1.8
- Added support to channel selection for resthook module @tiledesk-ent/tiledesk-server-resthook: 1.1.47
- Added supervisor role
- BugFix: Updated jwthistory and queue module with listen function fix (also in 2.1.14.1)
- Department patch method added (also in 2.1.14.2)
- BugFix: Now you can signupWithCustomToken using subject=userexternal and subscription type audience (https://tiledesk.com/subscriptions/subid). It's used by Whatsapp and Facebook Messenger apps (also in 2.1.14.2)
- Chat21 contact detail endpoint
- Added tags field for the lead model
- Added location field to the request model. Auto populate location field from ip
- Update all dependencies to last version
- Image endpoint now return also thumbnail filename
- Added analytics endpoint for messages (also in 2.1.14.2)
- New websocket return also events model (beta)
- Log fix for signup and signin endpoint (also in 2.1.14.2)
- Added email notification setting for each teammate (also in 2.1.14.3)
- Added email notification setting for each project
- Bugfix (@tiledesk-ent/tiledesk-server-triggers":1.1.69) for chatbot invitation race condition with Chat21 createGroup and setMembers method. Now the trigger listens to requestEvent.on("request.support_group.created",..) event and not to requestEvent.on("request.create",..) event. This doen't require data migration for old triggers (also in 2.1.14.4).
- Added plugin to save log to MongoDB (also in 2.1.14.4) with WRITE_LOG_TO_MONGODB=true, LOG_MONGODB_LEVEL, DATABASE_LOG_URI
- Added plugin to save multi-tenant log to MongoDB with WRITE_LOG_MT_TO_MONGODB=true, LOG_MT_MONGODB_LEVEL
- Added DEFAULT_FULLTEXT_INDEX_LANGUAGE env parameter for Faq, Lead, message and requests. Before the index language was Italian.
- Added support to \close action
- Disabled send trascript email for autoclosed conversations #413

# 2.1.14.5 -> Cloud Production
- Winston MongoDB Log fix

# 2.1.14.4
- Automatically close unresponsive bot conversation. You may configure CLOSE_BOT_UNRESPONSIVE_REQUESTS_CRON_EXPRESSION, etc.
- Bugfix (@tiledesk-ent/tiledesk-server-triggers":1.1.69) for chatbot invitation race condition with Chat21 createGroup and setMembers method. Now the trigger listens to requestEvent.on("request.support_group.created",..) event and not to requestEvent.on("request.create",..) event. This doen't require data migration for old triggers.
- Added plugin to save log to MongoDB 

# 2.1.14.3
Added email notification setting for each teammate (also in 2.1.14.3)

# 2.1.14.2
- Department patch method added (ok)
- BugFix: Now you can signupWithCustomToken using subject=userexternal and subscription type audience (https://tiledesk.com/subscriptions/subid). It's used by Whatsapp and Facebook Messenger apps . UNISALENTO TEST
- Added analytics endpoint for messages 
- Log fix for signup and signin endpoint.

# 2.1.14.1
- Updated queue module with listen function fix

# 2.1.14
- Renamed field presence.lastOnlineAt to changedAt
- Added filter presencestatus for project_users endpoint
- Websocket events updated with filters

# 2.1.13
- Added Cors options pre-flight with 
- Fix TD218 Audit log for user invitation already registered

# 2.1.12
- Chat21 engine selection with CHAT21_ENGINE=[native|firebase]
- Schema migration tool with mongoose-migrate. Added env property DISABLE_AUTO_SHEMA_MIGRATION
- #TD-250 Added emoji callout
- Cors fix. Removed alternative cors response header.
- Channel manager refactoring
- Event route fix and ws event endpoint
- WS projectì_user endpoint is now usable by other teammate
- Message text required only for type text messages
- #TD-251 Email lower case fix
- Updated Node default engine to 11.15.0
- Added hasBot query filter to retrive conversations with or without a bot
- Chatbot \frame action command supported
- Supported components: tiledesk-dashboard:2.0.73+ chat21-webwidget:4.0.75+ chat21-ionic:2.0.12

# 2.1.11
- Mongo support for Winston with: WRITE_LOG_TO_MONGODB=true 
- Logfix

# 2.1.10
- Tiledesk Chat21 groups syncronizer. Enable with SYNC_CHAT21_GROUPS="true"
- Built-in faq updated  and chatbot webhook example changed
- Return role: admin if the admin sign-in with email and password
- Default fallback event emitting
- Files and images storage services
- Supported components: tiledesk-dashboard:2.0.70 chat21-webwidget:4.0.73 chat21-ionic:2.0.12

# 2.1.9
- Widget departments fix

# 2.1.8
- SigninWithCustomToken fix for different audience types

# 2.1.7
- Minor fix

# 2.1.6 
- Push notification fix for the first support message and for group joining.

# 2.1.5
- Email template externalization with handlebars under /template/email folder. 
 You can override the email template using EMAIL_ASSIGN_REQUEST_HTML_TEMPLATE, EMAIL_POOLED_REQUEST_HTML_TEMPLATE,
 EMAIL_RESET_PASSWORD_HTML_TEMPLATE, EMAIL_PASSWORD_CHANGED_HTML_TEMPLATE, EMAIL_EXUSER_INVITED_HTML_TEMPLATE,
 EMAIL_NEWUSER_INVITED_HTML_TEMPLATE, EMAIL_VERIFY_HTML_TEMPLATE, EMAIL_SEND_TRANSCRIPT_HTML_TEMPLATE env variables

# 2.1.4
- Email config parameters fix

# 2.1.3
- Language pivot fix

# 2.1.2
- License fix

# 2.1.1
- Minor bug fix

# 2.1.0
- Release

# 2.1.0-beta24
- Minor bug fix

# 2.1.0-beta23
- Email fix for pooled request caming from bot

# 2.1.0-beta22 
- filter identity bot. use all=true to get all bot. Require Dashboard 2.0.49
- Chat21 Contacts for web chat recipients list
- Chat21 Presence webhook 
- Widget i8n


# 2.1.0-beta14 # 2.1.0-beta15 # 2.1.0-beta16 # 2.1.0-beta..20
- Docker tag

# 2.1.0-beta13
- add canned responses and tag library
- add groups and departments modules
- cache, routing, resthook deps update
- added request.status all for rest api
- request and lead physical deletion
- add mt and visitor counter modules
- removed reqLog feature
- typing webhook fix
- label fix with no pivoting to default languages
- removed terminus

# 2.1.0-beta12
- Send transcript fix

# 2.1.0-beta11
- Activity archiver fix for preflight request
- request physical deletion

# 2.1.0-beta10
- Minor bugfix for events

# 2.1.0-beta9
- Trigger fix for custom authentication

# 2.1.0-beta7
- Activities, Jwt History and Rest Hook update

# 2.1.0-beta6
- Widget language pivoting fix

# 2.1.0-beta5
- Support for cache
- Removed message_count of request model
- Concierge bot now update lead after preflight

# 2.1.0-beta4
- added isAuthenticated field to project_user model
- trigger update 
- set requester to request create of the chat21 webhook

# 2.1.0-beta2
- added field participantsAgents, participantsBot and hasBot fields. Migration file updated
- request, department, project, project_users, subscription indexes added
- conciergeBot multilanguage improvement
- trigger module updated
- resthook module updated with minor fixes
- added fanout pub sub to queue module and added support for *.queue.pubsub events
- WS_HISTORY_REQUESTS_LIMIT env variable added

# 2.1.0-beta1 
- project rest api order fix by updatedAt
- improved internal bot with defaultFallback and smart text and webhook
- messageService.send with metadata field
- widget and test page route
- Dockerfile fix (removed nano and nodemon)
- invite teammate rest api with available or unavailable 
- welcome message when a request is assigned to an agent (TOUCHING_OPERATOR)
- added department description and bot description fields
- added request rating rest api (PATCH)
- implemented \start command 
- trigger improvement 
- added request status (TEMP=50) and preflight field (exclude request.preflight=true from ws) 
- concierge bot now supports switch from preflight to standard request (rerouting, preflight update, first_text update) 
- added typing event 
- created Message Transformation Engine for multilanguage message (labels with the new labelService) and text templating
- added language field to message model and indexes improvement
- tag and tagLibrary refactoring 
- resigninAnonymously rest api for widget re-authenticate
- email notification improvement for agent joing 
- added label for office closed
- added queue for Enterprise version (websocket)
- Websocket pub/sub fix with handlePublishMessageToClientId
- Websocket performance fix with lean and removing populate 
- Added kubernetes sample config file
- Added required firstname and lastname to signup endpoint
- Removed message.request.messages and message.request.department.bot for message.create event  
