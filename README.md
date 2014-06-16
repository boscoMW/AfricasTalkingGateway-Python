AfricasTalkingGateway-Python
============================

A Python module for communicating with the AfricasTalking API

[Click here to read the full
documentation.](https://www.africastalking.com/tutorials/sendsms/python "Africastalking
Python library documentation")

## Installation

Install from PyPi using [pip](http://www.pip-installer.org/en/latest/), a
package manager for Python.

    pip install africastalking

Or, you can [download the source code
(ZIP)](https://github.com/twilio/twilio-python/zipball/master "AfricasTalkingGateway-python
source code") for `AfricasTalkingGateway-python`, and then run:

    python setup.py install

You may need to run the above commands with `sudo`.

## Getting Started

Getting started with the AfricasTalkingGateway API couldn't be easier. Create a
`AfricasTalkingGateway` and you're ready to go.

### API Credentials

The `AfricasTalkingGateway` needs your credentials. You can either pass these
directly to the constructor (see the code below) or via environment variables.

```python
from AfricasTalkingGateway import AfricasTalkingGateway, AfricasTalkingGatewayException

username = "MyAfricasTalking_Username";
apikey   = "MyAfricasTalking_APIKey";

gateway = AfricasTalkingGateway(username, apikey)
```

We suggest storing your credentials as environment variables. Why? You'll never
have to worry about committing your credentials and accidentally posting them
somewhere public.


### Send an SMS

```python
# Import the helper gateway class
from AfricasTalkingGateway import AfricasTalkingGateway, AfricasTalkingGatewayException

# Specify your login credentials
username = "MyAfricasTalking_Username";
apikey   = "MyAfricasTalking_APIKey";

# Specify the numbers that you want to send to in a comma-separated list
# Please ensure you include the country code (+254 for Kenya in this case)
to      = "+254711XXXYYYZZZ,+254733XXXYYYZZZ";

# And of course we want our recipients to know what we really do
message = "I'm a lumberjack and it's ok, I sleep all night and I work all day"

# Create a new instance of our awesome gateway class
gateway = AfricasTalkingGateway(username, apikey)

# Any gateway errors will be captured by our custom Exception class below, 
# so wrap the call in a try-catch block
try:
    # Thats it, hit send and we'll take care of the rest. 
    recipients = gateway.sendMessage(to, message)
    for recipient in recipients:
        # Note that only the Status "Success" means the message was sent
        print 'number=%s;status=%s;messageId=%s;cost=%s' % (recipient['number'],
                                                            recipient['status'],
                                                            recipient['messageId'],
                                                            recipient['cost'])
except AfricasTalkingGatewayException, e:
    print 'Encountered an error while sending: %s' % str(e)
```

### Digging Deeper

The full power of the AfricasTalkingGateway API is at your fingertips. The [full
documentation](https://www.africastalking.com/tutorials "AfricasTalking documentation") explains all the awesome features available to
use.
