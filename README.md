# Chatbot
Python chatbot AI that helps in creating a python based chatbot with
minimal coding. This provides both bots AI and chat handler and also
allows easy integration of REST API's and python function calls which
makes it unique and more powerful in functionality. This AI provides
numerous features like learn, memory, conditional switch, topic-based
conversation handling, etc.


![Demo](https://raw.githubusercontent.com/ahmadfaizalbh/Chatbot/master/images/demo.gif)
![Clothing assistance](https://raw.githubusercontent.com/ahmadfaizalbh/Chatbot/master/images/clothing.gif)
![Remainder](https://raw.githubusercontent.com/ahmadfaizalbh/Chatbot/master/images/reminder.gif)

## Installation

Install from PyPI:
```sh
pip install chatbotAI
```

install from github:
```sh
git clone https://github.com/ahmadfaizalbh/Chatbot.git
cd Chatbot
python setup.py install
```

## Demo
```python
>>> from chatbot import demo
>>> demo()
Hi, how are you?
> i'm fine
Nice to know that you are fine  
> quit
Thank you for talking with me.
>>> 
```

## Sample Code (with wikipedia search API integration)

```python
from chatbot import Chat,reflections,multiFunctionCall
import wikipedia

def whoIs(query,sessionID="general"):
    try:
        return wikipedia.summary(query)
    except:
        for newquery in wikipedia.search(query):
            try:
                return wikipedia.summary(newquery)
            except:
                pass
    return "I don't know about "+query
        
call = multiFunctionCall({"whoIs":whoIs})
firstQuestion="Hi, how are you?"
Chat("examples/Example.template", reflections,call=call).converse(firstQuestion)
```
