#! /urs/bin/env bash

## Discription: Create a docker image and delete the docker file and directory afterward
## Authur:Sheva@hotmail.com
## Revised by: max@hotmail.com  on 4/8/2022

echo "In what directory and name folder will your workspace be?"

read idirect

mkdir ${idirect} && cd ${idirect} && touch Dockerfile

echo "What is your base OS? (centos, alpine, or ubuntu )"

read osname

if [ ${osname} != centos ] || [ ${osname} != alpine ] || [ ${osname} != ubuntu ] || 
then 
echo "Please enter a valid choice between: centos, alpine or ubuntu"
exist 1
fi

echo "What port do you want to listing to ?"

read p 

echo "What version do you want to use ?"

read vers

if  [[ ${osname} = centos]];then
echo -e "FROM ${osname} : ${vers}""\nMAINTAINER: ${USER}""\nEXPOSE ${P}/tcp""\nRUN yum update -y" >
echo "Building ${osname} image."
 elif
 [[ ${osname} = alpine]];then
 echo -e "FROM ${osname} : ${vers}""\nMAINTAINER: ${USER}""\nEXPOSE ${P}/tcp""\nRUN apk update " >
 echo "Building ${osname} image."
  else
  if
  [[ ${osname} = ubuntu]];then
  echo -e "FROM ${osname} : ${vers}""\nMAINTAINER: ${USER}""\nEXPOSE ${P}/tcp""\nRUN apt-get update -y" >
  echo "Building ${osname} image."
fi
 fi

doker image buid -t ${USER}_${osname} .
if [[ $#! -eq 0]]
then
rm -f Dockerfile 
cd -
rm -r ${idirect}
echo -e "${osname} image built successfully. Also, Dockerfile and directory deleted.""\n Please run the docker images command to check."
exit 0
fi 
