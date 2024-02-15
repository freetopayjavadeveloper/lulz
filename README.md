# lulz

1)      
1/2   1./2   1/2.   1./2.  = ?
      
2)       
public abstract class Test implements Runnable {        
    private Object lock = new Object(); 
 
    public void lock() { 
        synchronized (lock) { 
            try { 
                lock.wait(); 
                System.out.println("1"); 
            } catch (InterruptedException e) { 
            } 
        } 
    } 
 
    public void unlock() { 
        synchronized (lock) { 
            lock.notify(); 
            System.out.println("2"); 
        } 
    } 
 
    public static void main(String s[]) { 
        new Thread(new Test() { 
            public void run() { 
                lock(); 
            } 
        }).start(); 
        new Thread(new Test() { 
            public void run() { 
                unlock(); 
            } 
        }).start(); 
    } 
}


3)        
public class Test {
    static void perform() {
    	System.out.println("perform");
    }

    private Test x;
    public static void main(String s[]) {
       x.perform(); // корректно ли это выражение?
    }
}

4)       
public class Overload {

  public void method(Object o) {
    System.out.println("Object");
  }

  public void method(java.io.FileNotFoundException f) {
    System.out.println("FileNotFoundException");
  }

  public void method(java.io.IOException i) {
    System.out.println("IOException");
  }

  public static void main(String args[]) {
    Overload test = new Overload();
    test.method(null);
  }
}

5)        
interface One {
   default void method1() {
       System.out.println("One-method1");
   }
   void method2();
}

@FunctionalInterface
interface Two extends One {
   default void method1() {
       System.out.println("Two-method1");
   }
}

public class TwoImpl implements Two {
   public void method2() {
       System.out.println("TwoImpl-method2");
   }

   public static void main(String[] args) {
       new TwoImpl().method1();
   }
}













