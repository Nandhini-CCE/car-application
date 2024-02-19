import java.time.LocalDateTime;
import java.util.ArrayList;
import java.util.Scanner;
class Cars{
    int carid;
    String cname;
    String oname;
    boolean availability;
    int rentprice;
    LocalDateTime dateTime;
    public Cars(String cname,String oname,int carid,boolean availability,int rentprice){
        this.carid=carid;
        this.cname=cname;
        this.oname=oname;
        this.availability=availability;
        this.rentprice=rentprice;
    }
    public LocalDateTime getBookDateTime(){
        return dateTime;
    }
    public void  setBookDateTime(LocalDateTime datetime){
        this.dateTime=datetime;
    }


}
public class Main {
    static Scanner sc=new Scanner(System.in);
    static ArrayList<Cars> carbook=new ArrayList<>();
    public static void main(String[] args){
        while(true){
            System.out.println("Car Booking Application");
            System.out.println("1.User Account");
            System.out.println("2.Display details of account");
            System.out.println("3.Display details of account which are available for rent");
            System.out.println("4.car booking");
            System.out.println("Enter the choice");
            int choice=sc.nextInt();
            switch(choice){
                case 1:
                    createacc();
                    break;
                case 2:
                    display();
                    break;
                case 3:
                    availablerentcar();
                    break;
                case 4:
                    carbooking();
                    break;
            }


        }
    }
    public static void createacc(){
        System.out.println("Enter car Id");
        int carid=sc.nextInt();
        sc.nextLine();
        System.out.println("Enter car name");
        String cname=sc.nextLine();
        System.out.println("enter owner name");
        String oname=sc.nextLine();
        System.out.println("enter car Availability");
        boolean avalability=sc.nextBoolean();
        sc.nextLine();
        System.out.println("enter car rent price");

        int rentprice=sc.nextInt();
        carbook.add(new Cars(cname,oname,carid,avalability,rentprice));
        System.out.println("Account has been created successfully");
    }
    public static  void display(){
        if(carbook.isEmpty()){
            System.out.println("There is no account");
            return;
        }
        else{
            System.out.println("the account details are");
            for(Cars i:carbook){
                System.out.println(i.carid);
                System.out.println(i.cname);
                System.out.println(i.oname);
                System.out.println(i.availability);
                System.out.println(i.rentprice);
                System.out.println("---------------------------------------------------");

            }
        }
    }
    public static  void availablerentcar(){
        if(carbook.isEmpty()){
            System.out.println("There is no account");
            return;
        }
        else{
            System.out.println("the available rent car are");
            for(Cars i:carbook) {
                if (i.availability ==true) {
                    System.out.println(i.carid);
                    System.out.println(i.cname);
                    System.out.println(i.oname);
                    System.out.println(i.availability);
                    System.out.println(i.rentprice);
                    System.out.println("---------------------------------------------------");

                }
            }
        }
    }
    public static void carbooking(){
        if(carbook.isEmpty()) {
            System.out.println("There is no account");
            return;
        }
            else{
                System.out.println("Enter car id to for booking");
                int carId=sc.nextInt();
                for(Cars i:carbook){
                    if(i.carid==carId && i.availability){
                        System.out.println("Enter Date and time for booking");
                        String bookdate=sc.next();
                        LocalDateTime datetime=LocalDateTime.parse(bookdate.replace(" ","T"));
                        i.setBookDateTime(datetime);
                        i.availability=false;
                        System.out.println("Car booked successfully!");
                        return;
                    }

                    }
                }

    }


}
