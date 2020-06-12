class Main {
  public static void main(String[] args) {
    int n=2;
    char [] arr=new int [n*2]; 
    forward(n,0,0,arr);
  }
  static void forward(int n,int forw,int backw,char [] arr){ //兩種狀況
    forw++;
    arr[forw+backw]='(';
    if(forw<n){ //前括號還有剩  (n:3 forw:1)
      forward(n,forw,backw,arr);
      backward(n,forw,backw,arr);
    }
    if(forw==n){ //前括號用完了 (n:3 forw:3)
      backward(n,forw,backw,arr);
    }
  }
  static void backward(int n,int forw,int backw,char [] arr){ //三種狀況
    backw++;
    arr[forw+backw]=')';
    if(backw==n){
      for(char i:arr)
      System.out.println();////////////////
    }
    if(backw==forw && forw<n){ // 只有forw能++ (n:3 forw:1 backw:1)
      forward(n,forw,backw,arr);
    }
    if(backw<forw && forw==n){ // 只有backw能++ (n:3 forw:3 backw:1)
      backward(n,forw,backw,arr);
    }
    if(backw<forw && forw<n){ // forw && backw能++ (n:3 forw:1 backw:0)
      forward(n,forw,backw,arr);
      backward(n,forw,backw,arr);
    }
  }
}
