# Use Case: Web of Needs

[Web of Needs (WoN)](https://matchat.org/) lets users post RDF structures to describe their interest in interactions. 

Independent matchers find posts (=needs) that may be suitable for an interaction and send 'hint' messages to the postings, which can be seen by the users.

Users can then start communicating by exchanging messages that can contain arbitrary RDF.

Thus, we have 4 main points where we'd like to use rdfruit:

## 1. Create Posting

Generate arbitrary RDF, ideally using the perfect user-friendly GUI.

Example: I want to get from my current location to point B

## 2. Display a Posting when matched 

Render a GUI from a priori unknown RDF, ideally in a way that fits the user's context

Example: Someone is nearby and would drive me to B if I'm quick enough to hop on within 3 minutes.

## 3. Author a message 

Generate arbitrary RDF, ideally using the perfect user-friendly GUI.

Example: confirm an appointment: in 3 minutes at location A

## 4. Display a message 

Render a GUI from a priori unknown RDF, ideally in a way that fits the user's context

Example: Show that the other user has confirmed my suggestion for an appointment in 3 minutes at location A


## Requirements for the UI Layer

### 1. Discovery of UI components

In WoN, you can post and find anything. The only thing you'll know about postings or messages a priori is that they are RDF datasets. They will have a few standard triples, but these don't normally interest users. Consequently, it is not feasible to prepare a UI library for authoring every conceivable WoN posting. Rather, we'd like a discovery system that finds the right UI component on the fly. For that to be possible, the components need to be adaptive in terms of visual style, language, context (whatever that is exactly - it is a thing). 

Moreover, the components must not pose a security risk in any way, e.g. component lookup shouldn't send sensible data like the user's location, passwords, etc. Also, we should look into ways to support managing permissions for components to prevent access to and sending of sensitive data without the user's permission.

### 2. Generic RDF authoring capabilities

For situations in which no GUI components can be found, generic tools are needed for content authoring. The requirements for those components are the same as in 1. In addition to that, the generic tools should allow non-RDF savvy Web users to author simple RDF structures.

### 3. Consistent Style

Applications using the system should still have a coherent visual style and adhere to typical user interface patterns to make the application more accessible and coherent with learned interface design language. A way forward here might be to split styling (e.g. color, border-radius, etc) from layouting (flex, grid, etc). Other alternatives could be parametrizing components with style variables or using a consistent style "API" (e.g. bootstrap or semui class-names, or even a different, intermediary language). This should allow instances of the framework to apply their own CI/skinning/look-and-feel without breaking the widget's layout. 

### 4. Mobile-First

For the usual-reasons<sup>[1](#user-content-fn1)</sup> it should be possible to start on mobile platforms. This means responsive components as well as being able to work with flaky and low-bandwidth connections (e.g. components can't be 1M each)

<a id="fn1">[1]</a>: mobile internet usage constitute more than 50% of the overall usage and it's easier to move from a mobile design to a desktop version than the other way around
