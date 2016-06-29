#!/bin/bash

if [[ "$1" == "" || ! -d "$1" ]] ;
then
  echo "no folder exists, please check it."
  exit
fi

dir=$1
dirname=`basename $dir`
append=md5
action="echo \$f"
mdir=${bdir}${append}

if [ "$dir" == "$mdir" ] ;
then
  echo "something is wrong..."
  exit
fi

if [ -f "$dirname" ] ;
then
  echo "this is not a folder, weird stuff happened."
  exit
fi

for f in `find $dir -type f`;
do
  mpath=`dirname $f | sed 's/'$dirname'/'$dirname'md5/'`
  mname=`basename $f`
  fmd5=`cat $mpath/$mname`
  if [ "$fmd5" != "`md5sum $f | awk '{print $1}' `"  ] ;
  then
    eval $action
  fi
done
