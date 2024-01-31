# hashicorp_terraform_initiator
A shell invoker to make your HCL hashicorp programming easy and to write the init files easy for any instance and to deploy them on the cluster integration. simply provide the instance name and the routing cluster and the deployment zone mode and it will make the hashicorp deployment variable declaration and the invokation file. 

make any number of the hashicorp terraform instance either by directory providing the region, user and the interface or by providing the file with the network route.  I integrated the C and releasing a new add on in C++ also for the same and you can invoke that on any instance provider. This is blazing fast and you dont need a new console for the same. You can change to any separator in the second code instead of ",".
```
#! /usr/bin/bash
# Universitat Potsdam
# Author Gaurav Sablok
# date: 2024-1-24
# generating the terraform installation files
read -r -p "please provide the link region:" region
read -r -p "please provide the number of the networks ipinterface:" ipinterface
read -r -p "please provide the provider:" provider
read -r -p "please provide the instance name:" name
read -r -p "please provide the ami:" ami
read -r -p "please provide the instance name:" instance
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
       echo "aws_instance "${name}" {
      ami = "${ami}"
      instance_type = "${instance}"
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
    echo "aws_instance "${name}" {
      ami = "${ami}"
      instance_type = "${instance}"
       }"
done
```
2024-1-30: added a specific code for the complete aws deployment with the instance name and the ami support. 

Gaurav Sablok, \
Academic Staff Member, \
Bioinformatics,\
Institute for Biochemistry and Biology, \
University of Potsdam, \
Potsdam,Germany
