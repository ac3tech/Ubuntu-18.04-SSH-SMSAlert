# SMS Alert

Texts you when someone logs into your ubuntu server (this is my first post sorry if it looks like crap ;) )

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

1. **PostFix and it's requirements**

```
sudo apt install mailutils
```
For additional help with setting up PostFix: https://computingforgeeks.com/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-18-04-lts/



2. **Your Cellphone providers Email to SMS**
    * https://teamunify.uservoice.com/knowledgebase/articles/57460-communication-email-to-sms-gateway-list
  
  
3. **Git and its requirements**
```
sudo apt install git
```

### Installing

**Clone the Repository**

```
git clone https://github.com/ac3tech/Ubuntu-18.04-SSH-SMSAlert.git && cd Ubuntu-18.04-SSH-SMSAlert 
```

**Edit smsalert.sh and configure your providers email to sms**
```
sudo nano smsalert.sh
```
**Edit "5555555555@yourprovider.com and input your providers sms to email**
```
if [ -n "$SSH_CLIENT" ]; then
    TEXT="$(date): ssh login to ${USER}@$(hostname -f)"
    TEXT="$TEXT from $(echo $SSH_CLIENT|awk '{print $1}')"
    echo $TEXT|mail -s "ssh login" YourPhoneNumber@yourprovider.com
fi
```
**Move smsalert.sh to profile.d**
```
sudo cp smsalert /etc/profile.d
```


## Running the tests

To test and see if you have everything setup correctly simply logout and log back into your server if you get a text you know that you have it setup correctly 
```
logout
```

## Built With
* [PostFix](www.postfix.org/) - Too send an email to your providers email to sms


## Authors

* **Andrew Edson** - [Ac3 Tech](https://github.com/ac3tech)


## License

This project is licensed under the GNU License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

**Feel free to donate** 
Paypal: andrew.edson3@hotmail.com -- Bitcoin: coming soon!!!

