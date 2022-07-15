package main
import "fmt"
func main(){
    var(
        s string
        a int = 0
        b int = 0
        sum int = 0
        c rune
    )
    flag:=1
    g:=1
    fmt.Scanf("%s", &s)
    for i:=0;i<len(s);i++{
        if s[i]=='+'{
            sum=sum+a*flag
            a=0
            flag=g
        } else if s[i]=='-' {
            sum=sum+a*flag
            a=0
            flag=-g
        } else if s[i]=='=' {
            sum=sum+a*flag
            flag=-1
            a=0
            g=-1
        } else if s[i]<='z' && s[i]>='a' {
            c=rune(s[i])
            if a==0{
                b=b+flag
            } else {
                b=b+a*flag
                a=0
            }
        } else{
            a=a*10+int(s[i])-'0'
            if i==len(s)-1 {
                sum=sum+a*flag
            }
        }
    }
    sum=-sum
    if (float64(sum)/float64(b))==0 {
        fmt.Printf("%c=0.000",c)
    } else{
        fmt.Printf("%c=%.3f",c,float64(sum)/float64(b))
    }
    
}