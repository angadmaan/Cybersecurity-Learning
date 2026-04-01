# OSI MODEL 

The OSI model has 7 layers.

- 7 (Application)  
- 6 (Presentation)  
- 5 (Session)  
- 4 (Transport)  
- 3 (Network)  
- 2 (Data Link)  
- 1 (Physical)  

## Purpose
The OSI model helps understand that how data travels across a network.

## OSI: A Layered Network Model

- The process of breaking up the functions or tasks of networking into layers reduces complexity.
- Each layer provides a service to the layer above it in the protocol specification.
- Each layer communicates with the same layer’s software or hardware on other computers. 
- The lower 4 layers (transport, network, data link and physical —Layers 4, 3, 2, and 1) are concerned with the flow of data from end to end through the network. 
- The upper four layers of the OSI model (application, presentation and session—Layers 7, 6 and 5) are orientated more toward services to the applications. 
- Data is Encapsulated with the necessary protocol information as it moves down the layers before network transit.

### Physical Layer 
- Provides physical interface for transmission of information.
- Defines rules by which bits are passed from one system to another on a physical communication medium.
- Covers all - mechanical, electrical, functional and procedural - aspects for physical communication.
- Such characteristics as voltage levels, timing of voltage changes, physical data rates, maximum transmission distances, physical connectors, and other similar attributes are defined by physical layer specifications. 

### Data Link Layer
- Data link layer attempts to provide reliable communication over the physical layer interface. 
- Breaks the outgoing data into frames and reassemble the received frames.
- Create and detect frame boundaries.
- Handle errors by implementing an acknowledgement and retransmission scheme.
- Implement flow control.
- Supports points-to-point as well as broadcast communication.
- Supports simplex, half-duplex or full-duplex communication.

### Network Layer
- Implements routing of frames (packets) through the network.
- Defines the most optimum path the packet should take from the source to the destination
- Defines logical addressing so that any endpoint can be identified. 
- Handles congestion in the network.
- Facilitates interconnection between heterogeneous networks (Internetworking).
- The network layer also defines how to fragment a packet into smaller packets to accommodate different media.

### Transport Layer
- Purpose of this layer is to provide a reliable mechanism for the exchange of data between two processes in different computers. 
- Ensures that the data units are delivered error free.
- Ensures that data units are delivered in sequence.
- Ensures that there is no loss or duplication of data units.
- Provides connectionless or connection oriented service.
- Provides for the connection management.
- Multiplex  multiple connection over a single channel.

### Session Layer
- Session layer provides mechanism for controlling the dialogue between the two end systems. It defines how to start, control and end conversations called sessions between applications.
- This layer requests for a logical connection to be established on an end-user’s request.
- Any necessary log-on or password validation is also handled by this layer.
- Session layer is also responsible for terminating the connection.
- This layer provides services like dialogue discipline which can be full duplex or half duplex.
- Session layer can also provide check-pointing mechanism such that if a failure of some sort occurs between checkpoints, all data can be retransmitted from the last checkpoint.

### Presentation Layer
- Presentation layer defines the format in which the data is to be exchanged between the two communicating entities. 
- Also handles data compression and data encryption (cryptography).

### Application Layer 
- Application layer interacts with application programs and is the highest level of OSI model.
- Application layer contains management functions to support distributed applications.
- Examples of application layer are applications such as file transfer, electronic mail, remote login etc.

## OSI in Action
- A message begins at the top application layer and moves down the OSI layers to the bottom physical layer. 
- As the message descends, each successive OSI model layer adds a header to it. 
- A header is layer-specific information that basically explains what functions the layer carried out. 
- Conversely, at the receiving end, headers are striped from the message as it travels up the corresponding layers.





