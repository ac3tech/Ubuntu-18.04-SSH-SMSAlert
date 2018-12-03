# SMS Alert

Texts you when someone logs into your ubuntu server

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

1. **PostFix and it's requirements**

```
sudo apt install mailutils
```
For additional help with settingup PostFix: https://computingforgeeks.com/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-18-04-lts/



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

Explain how to run the automated tests for this system

### Break down into end to end tests

Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used
* Inspiration
* etc

