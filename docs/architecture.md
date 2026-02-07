## Product choice

* Telegram
* [Telegram Web](https://web.telegram.org/k/)
* Telegram (also known as Telegram Messenger) is a cloud-based, cross-platform social media and instant messaging (IM) service.

## Main components

![Telegram Component Diargam](../docs\diagrams\out\telegram\component-diagram\Component%20Diagram.svg)
[Link to Component Diagram PlantUml code](../docs\diagrams\src\telegram\component-diagram.puml)

### Components

1. Mobile app: it is an app of Telegram, which you can download on your device.
2. Bot API Server: it is a connection layer that handles requests to the Telegram Bot API.
3. Channel/Broadcast Service: it is a core service which handles with channels and broadcasts in telegram.
4. State Cache (Redis): this is an external storage for your bot's "states" and temporary data.
5. Secret Chat Relay: it is the role of Telegram servers in Secret Chats.

## Data Flow

![Telegram Sequence Diagram](../docs\diagrams\out\telegram\sequence-diagram\Sequence%20Diagram.svg)
[Link to Sequence Diagram PlantUml code](../docs\diagrams\src\telegram\sequence-diagram.puml)

### Media Upload Process

* Select Photo & Send
* Saves file
  * MTProto Gateway: this is the entry point. The client splits the file into parts
* Streams File Data
  * Auth Service checks the session once when the connection is established
* Writes Files Chunk (Message Service and Push Service)
* It goes to Data and check if everything is fine
* If it is then it saves File Metadata
* Part Saved and ACK(Part Saved)
* App repeats until file is fully uploaded.

## Deployment

![Telegram Deployment diagram](../docs\diagrams\out\telegram\deployment-diagram\Deployment%20Diagram.svg)
[Link to the Deployment diagram PlauntUML code](../docs\diagrams\src\telegram\deployment-diagram.puml)

The mobile app can be installed on users smartphone or computer. MTProto Gateway and Bot API Fronted are in Connection Layer. They are connected to Computer Cluster. In Computer Cluster there is Pod/Container with Services. It is connected to different Memory Clusters. Besides, there is an External Ecosystem.

## Assumptions

* I assume that State Cache is for temporary data.
* I assume that the file splits into parts while Media Upload.

## Open questions

* What does 3rd Parts Bot Servers do?
* How does push provider work?
