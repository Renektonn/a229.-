class Main {
  public static void main(String[] args) {
    int n=2;
    forward(n,0,0);
  }
  static void forward(int n,int forw,int backw){ //兩種狀況
    forw++;
    System.out.print('(');
    if(forw<n){ //前括號還有剩  (n:3 forw:1)
      forward(n,forw,backw);
      backward(n,forw,backw);
    }
    if(forw==n){ //前括號用完了 (n:3 forw:3)
      backward(n,forw,backw);
    }
  }
  static void backward(int n,int forw,int backw){ //三種狀況
    backw++;
    System.out.print(')');
    if(backw==forw && forw<n){ // 只有forw能++ (n:3 forw:1 backw:1)
      forward(n,forw,backw);
    }
    if(backw<forw && forw==n){ // 只有backw能++ (n:3 forw:3 backw:1)
      backward(n,forw,backw);
    }
    if(backw<forw && forw<n){ // forw && backw能++ (n:3 forw:1 backw:0)
      forward(n,forw,backw);
      backward(n,forw,backw);
    }
  }
}
