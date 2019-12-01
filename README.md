# ua
 
![alt text][logo]

![alt text][status]

user agent for remote laboratories

## Background

Remote laboratories require a user to connect to remote digital resources so as to exchange video, data and control commands. In some cases, remote operation of e.g. serial devices can be achieved with a utility such as [ser2net](https://github.com/gopherjs/websocket), although this does little to address the challenge of managing the complexity and ephemerality typical of large remote laboratories. Remote laboratory connection and communication procedures are not currently standardised either, so there is little hope of experiments and interfaces from disparate laboratoties being able to communicate without some interface to translate between them. 

### System complexity

The user agent ```ua``` is intended to shield users from system complexity so that legacy and new interfaces remain usable but are not subject to any additional maintenance or re-deployment burden. In a large, distributed remote laboratory, particularly one that is not owned or operated by a single entity, it is expected that operating procedures will have evolved to handle a degree of generality that is not necessarily present in a typical legacy single-site or finite-site-count lab consortium. For example, there may be optimisations to the way that data relays are used to accommodate restrictive network permissions and to exploit cheaper, short-lived spot-priced servers for that service. In such cases, long sessions would be comprised of multiple shorter sessions, each with distinct connection details but requireing to be seamlessly stitched together. In this case, a legacy native application may be unable to cope, because it might expects a local resource to be available at a particular static address, it may not be able to authenticate, or rely on outdated or unavailable forms of authorisation, and it may not support encrypted communications. In these cases, integration into a remote laboratory network can be retrieved without modification to the original interface code, by employing a user agent that abstracts away the communications with the external remote laboratory infrastructure, allowing a remote resource to masquerades as a local resource.

## Main use cases

Experiments neither know nor care about the presentation details of the user interfaces used to access them, so there is no barrier to supporting both native operating system applications, and browser based interfaces. 

![alt text][uses]

### Browser interface

#### Con: 
0. Not all experiment interfaces can be translated to the browser e.g. some proprietary languages are not available to program online

#### Pro
0.  Reduced technical support and deployment burden on suppliers and consumers due to convenience and immediacy of browser delivery

### Native interface

#### Con
0. requires separate deployment steps (download and install)
0. some consumers will complain your code broke their machine
0. different operating systems often need explicit handling

#### Pro
0. facilitates non-browser experiences such as legacy exectuable clients
0. offers industrial tools that are unavailable in the browser, such as programming environments


## Implementation

A number of programming languages (including golang) are readily [cross-compiled](https://github.com/gopherjs/websocket) to work on major operating systems and architectures, including the possibility of also compiling into [web-assembly](https://github.com/gopherjs/websocket). It appears that specific browser-aware libraries may be required for [websockets](https://github.com/gopherjs/websocket) so building / deployment may involve a different configuration/build set up for browser versus native implementations.


[logo]: ./img/logo.png "ua logo, person in square"
[uses]: ./img/uses.png "browser and native uses are envisages"
[status]: https://img.shields.io/badge/concept-development-red "Concept development" 

