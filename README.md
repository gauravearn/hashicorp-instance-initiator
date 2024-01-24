# hashicorp_terraform_initiator
A shell invoker to make your HCL hashicorp programming easy and to write the init files easy for any instance and to deploy them on the cluster integration. simply provide the instance name and the routing cluster and the deployment zone mode and it will make the hashicopr deployment variable declaration and the invokation file. 

```
#! /usr/bin/bash
# Universitat Potsdam
# Author Gaurav Sablok
# date: 2024-1-24
# generating the terraform installation files
read -r -p "please provide the link region:" region
read -r -p "please provide the number of the networks ipinterface:" ipinterface
read -r -p "please provide the provider:" provider
if [[ ${interface} == "ipaddress" ]]; then
    count=0
    interfacelink=()
    while [[ "${count}" -le "${ipinterface}" ]]; do
        read -r -p "please provide the network interface:" interface
        interfacelink+=("${interface}")
        ((count++))
    done
    echo "the provided interfaces are: ${interfacelink[*]}"
    for i in ${interfacelink[*]}; do
        echo "provider "${provider}" {
     profile =  "${i}"
     region  = "${region}"
}"
    done
elif [[ ${interface} = "file" ]]; then
    read -r -p "please provide the file name for the interface:" filename
    read -r -p "please provide the region for the instance creation:" region
    if [[ -f ${filename} ]]; then
        echo "the file is present"
        interfacelink=()
        for i in $(cat "${filename}" | cut -f 1 -d ","); do
            interfacelink+=("${i}")
            if [[ "${i}" == "" ]]; then
                break
            fi
        done
    fi
fi
for i in ${interfacelink[*]}; do
    echo "provider "${provider}" {
     profile =  "${i}"
     region  = "${region}"
}"
done
```

Github:https://github.com/sablokgaurav \
ORCID: https://orcid.org/0000-0002-4157-9405 \
WOS: https://www.webofscience.com/wos/author/record/C-5940-2014 \
RubyGems Published: https://rubygems.org/profiles/sablokgaurav \
Python Packages Published : https://pypi.org/user/sablokgaurav/ \
Crystal Profile: https://forum.crystal-lang.org/u/sablokgaurav/ \
devProfile: https://app.daily.dev/sablokgaurav \
