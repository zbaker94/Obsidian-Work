### Screen Resolution
Toughbook resolution: 1920x1200
Toughbook default scaling: 150%
Job's surface default scaling: 200%

### IT HR Email 
IT HR Sick email:  email it.hr@Claytoncountyga.gov

### Script to get auth token
```bash
#/bin/bash
curl -X POST -H "Content-Type: application/json" \
    -d '{  "userName": "zack.baker",  "userPassword": "KLDNBEE4RY!",  "moduleID": 1 }' \
    https://magistratecourtgateway-dev.claytoncountyga.gov/login | cut -d ":" -f 2 | cut -d "}" -f 1 | cut -d '"' -f
```




