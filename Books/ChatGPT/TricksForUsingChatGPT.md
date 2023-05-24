# Tricks for better answers from ChatGPT

## Step 1: Enter this prompt

> You are at the world debate championship. The motion of the debate is “This house supports universal income for all citizens”. The coalition are in favor of the motion. Think about arguments in favor of the motion, using a hierarchical table of contents that classify the arguments to at least 3 topics, then write the speech of the coalition. Then do the same for the opposition, who should argue against the arguments of the coalition.

## Step 2: Enter this prompt

> Now write the speech of the coalition, and the speech of the opposition. Start with the words “Ladies and gentlemen

## Bonus Trick

>As an advanced bonus trick, you can visualize the table of content as a graphical chart, by prompting ChatGPT for a mindmap in MermaidJS format, and pasting the result in <https://mermaid.live/>.

This annotation is from MVC/Web that will associate a given URI with a method in the controller. It can be used in the following format.

@RequestMapping(method = RequestMethod.PATCH)

---------------------------

@RequestBody
This annotation is used to bind a method parameter/object to incoming request parameters.

@ResponseBody
This is used inside a controller and signifies that the returned object will be automatically serialized and passed back into the HttpResponse object. Note that if you are using @RestController you may not need to use this as automatically it is a combination of @Controller and @ResponseBody.

@RequestParam
This is used to bind a method parameter directly to a request attribute.

@RequestHeader
This is used to bind a method parameter directly to a request header.

@RequestAttribute
This can be used to bind a method parameter to a request attribute that was added from an intermediary layer like filter or interceptor.

@PathVariable
This is used to bind a method parameter from a request template URI. Note that It can be used to bind multiple method parameters.