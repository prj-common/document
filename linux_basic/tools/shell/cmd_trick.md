#cd alias
alias ..="cd .."  
alias ..2="cd ../.."  
alias ..3="cd ../../.."  
alias ..4="cd ../../../.."  
alias ..5="cd ../../../../.."  
alias ..6="cd ../../../../../.."  
alias ..7="cd ../../../../../../.."  
alias ..8="cd ../../../../../../../.."  
alias ..9="cd ../../../../../../../../.."  

#mkdircd
function mkdircd () { mkdir -p "$@" && eval cd "\"\$$#\""; }
