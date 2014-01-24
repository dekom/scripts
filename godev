# usage: source godev root
#
# root is a root directory of your Go workspace, as described here:
# http://golang.org/doc/code.html
#
# The script will create the following directories:
# - root
# - root/bin
# - root/pkg
# - root/src
#
# Additionally, it also modify the following environment variables:
# - set/modify GOPATH to root
# - append root/bin to the end of PATH

if [ -z $1 ]; then
    echo "ERROR: empty directory supplied"
    return
fi

gopath=$(cd $(dirname "$1"); pwd)/$(basename $1)
subs="src pkg bin"

# create directory structure
echo "creating directory structure:"
for dir in $subs
do
    echo "$gopath/$dir"
    mkdir -p $gopath/$dir
done
echo

# setting environment variables

echo "setting environment variables:"
export GOPATH=$gopath
echo "GOPATH=$GOPATH"

# Add the ./bin directory to path
# reset to previous paths, otherwise bin paths stack
[ $GO_OLD_PATH ] && export PATH=$GO_OLD_PATH

gopathbin="$gopath/bin"

export GO_OLD_PATH=$PATH
export PATH=$PATH:$gopathbin
echo "PATH=$PATH"
