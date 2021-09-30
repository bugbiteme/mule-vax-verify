# mule-vax-verify
Process layer API that calls mule-vax-status system layer APIs, and verifies if fully, partially vaccinated or if record not found


## Sample calls for testing
```
curl --location --request GET 'http://mule-vax-verify.us-w1.cloudhub.io/api/verify-vaccine?firstName=John&lastName=Talksalot&dob=1981-10-25'

curl --location --request GET 'http://mule-vax-verify.us-w1.cloudhub.io/api/verify-vaccine?firstName=Jack&lastName=Sheppard&dob=1992-05-18'

curl --location --request GET 'http://mule-vax-verify.us-w1.cloudhub.io/api/verify-vaccine?firstName=Aden&lastName=Episcopio&dob=1994-09-11'

curl --location --request GET 'http://mule-vax-verify.us-w1.cloudhub.io/api/verify-vaccine?firstName=Max&lastName=Mule&dob=1991-04-06'
```

## Sample output from the above

```
{
  "vaccineStatus": "partially-vaccinated",
  "firstName": "John",
  "lastName": "Talksalot",
  "dob": "1981-10-25",
  "doses": [
    {
      "provider": "WALGREENS",
      "doa": "4/19/21",
      "lotNumber": "5678",
      "type": "Moderna"
    }
  ]
}
```

```
{
  "vaccineStatus": "fully-vaccinated",
  "firstName": "Jack",
  "lastName": "Sheppard",
  "dob": "1992-05-18",
  "doses": [
    {
      "provider": "LAX",
      "doa": "3/22/21",
      "lotNumber": "1234",
      "type": "Pfizer"
    },
    {
      "provider": "WALGREENS",
      "doa": "4/19/21",
      "lotNumber": "5678",
      "type": "Pfizer"
    }
  ]
}
```

```
{
  "vaccineStatus": "fully-vaccinated",
  "firstName": "Aden",
  "lastName": "Episcopio",
  "dob": "1994-09-11",
  "doses": [
    {
      "provider": "CVS",
      "doa": "5/25/21",
      "lotNumber": "1234",
      "type": "Johnson & Johnson"
    }
  ]
}
```

```
{
  "vaccineStatus": "not-found"
}
```
