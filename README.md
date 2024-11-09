#include<fstream>
#include<iomanip>
#include<windows.h>
#include<conio.h>
#include <ctype.h>
#include<stdlib.h>
#include<iostream>
#include<cstring>
#include<stdio.h>
using namespace std;
void WaitKey();
void gotoXY(int x, int y);
HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
COORD CursorPosition;
static int a;        //class specifications
class staff_login;
class student_login;
class register_now
{
	string name[10];
	public:
		int notice();
		int instructionsform();
		int registration_form();
		int confirmform();
		int routes();
		friend student_login;
		friend staff_login;
};
class student_login
{
	public:
		int login();
		int allotmentform();
		int contactdetails();
		int complaints();
		friend register_now;
};
class staff_login
{
	public:
		int login();
		int complaintbox();
		int notice();
		int allot_staffr();
};
int staff_login::login()
{
	register_now r1;
	staff_login s1;
	student_login s2;

	int u;
	string a[100],user1,user2,user3;
	char line[80];
	system("cls");
	cout<<"\n\n\n\n\n\n\n\n\n\n                    USERNAME:";
	cin>>user1;
	int i=0;
	char pwd[5];
	cout<<"                    PASSWORD:";
	while(i<4)
	{
		pwd[i]=getch();
		putchar('*');
		++i;
	}
	int j=0;
	user2=pwd;
	user3=user1+user2;
	ifstream fil5;
	fil5.open("login.txt",ios::out);
	while(fil5)
	{
		fil5.getline(line,80);
		a[j]=line;
		j++;
	}
	for(int k=0;k<50;k++)
	{
		if(a[k]==user3)
		{
		while(1)
		{
			system("cls");
			cout<<"\n\n WELCOME TO "<<user1;
			cout<<"\n\n\n\n\n\n                     1.Complaint Box"<<"\n                     2.Edit notice";
			cout<<"\n                     3.Routes with alloted staff";
			cout<<"\n                     4.To LOGOUT";
			cout<<"\n\n\n Select Your Option: ";
			cin>>u;
			switch(u)
			{
				case 1:system("COLOR 0F");
				s1.complaintbox();
						 break;
				case 2:system("COLOR 0F");
				s1.notice();
						break;
				case 3:system("COLOR 0F");
				s1.allot_staffr();
						break;
				case 4:system("COLOR 0F");
				system("cls");
						cout<<"\n\n\n\n\n\n\n           LOADING PLEASE WAIT ... ";
						Sleep(500);
						return 0;
				default:return 0;
			}
		}
	}
}
	system("cls");
		cout<<"\n\n\n      SORRY,"
			<<"\n      invalid username or password";
		Sleep(300);
	return 1;
}
int staff_login::notice()
{
	system("cls");
	fstream fin;
	fin.open("program.txt",ios::out | ios::app );
	fin<<endl;
	string mystr;
   	getline (cin, mystr);
  	cout << "Enter the Notice :";
  	getline (cin, mystr);
  	fin<<mystr;
  	cout<<"\n\n\n\nEnter any key to return main menu :";
  	getch();
  	return 1;
}

int staff_login::complaintbox()
{
	char ch;
	system("cls");
	ifstream fin6;
	fin6.open("complaintbox.cpp",ios::in);
	while(fin6)
	{
		fin6.get(ch);
		cout<<ch;
	}
	cout<<"\n\n\n\n\n\n   Enter the any key to return to main menu";
	getch();
	return 1;
}
int staff_login::allot_staffr()
{
	system("cls");
	char ch;
	ifstream fin6;
	fin6.open("allotedstaff.cpp",ios::in);
	while(fin6)
	{
		fin6.get(ch);
		cout<<ch;
	}
	cout<<"\n\n\n\n\n\n   Enter the any key to return to main menu";
	getch();
	return 1;
}
int student_login::login()
{
	register_now r1;
	staff_login s1;
	student_login s2;

	int u;
	string a[100],user1,user2,user3;
	char line[80];
	system("cls");
	cout<<"\n\n\n\n\n\n\n\n\n\n                    USERNAME:";
	cin>>user1;
	int i=0;char ch;
	char pwd[5];
	cout<<"                    PASSWORD:";
	while(i<4)
	{
		pwd[i]=getch();
		putchar('*');
		++i;
	}
	int j=0;
	user2=pwd;
	user3=user1+user2;
	ifstream fil5;
	fil5.open("login.txt",ios::out);
	while(fil5)
	{
		fil5.getline(line,80);
		a[j]=line;
		j++;
	}
		for(int k=0;k<50;k++)
		{
		if(a[k]==user3)
		{
		while(1)
		{
			system("cls");
			cout<<"\n\n WELCOME TO "<<user1;
			cout<<"\n\n\n\n\n                  1.Allotment form";
			cout<<"\n                  2.Complaint"<<"\n                  3.Staff contact details";
			cout<<"\n                  4.To LOGOUT";
			cout<<"\n\n\n\n\n\n Select Your Option: ";
			cin>>u;
			switch(u)
				{
				case 1:s2.allotmentform();
						break;
				case 2:s2.complaints();
						break;
				case 3:s2.contactdetails();
						break;
				case 4:system("cls");
						cout<<"\n\n\n\n\n\n\n            PLEASE WAIT ... LOADING";
						Sleep(500);
						return 0;
				default:exit;
				}
			}
    	}
    }
		system("cls");
		cout<<"\n\n\n      SORRY,"
			<<"\n      invalid username and password";
		Sleep(300);
	return 1;
}
int student_login::allotmentform()
{
	system("cls");
	string j,tem[10];
	int i,d;
	cout<<"Enter your Username :";
	cin>>j;
	ifstream f8;
	f8.open("list_of_students",ios::in);
	f8.seekg(0,ios::beg);
	while(!f8.eof())
    {
        i++;
        string temp;
        f8 >> temp;
        if(temp == j)
        {
            d=f8.tellg();
            break;
        }
	}
	int y=d+6;
	int l=0;
	while(d!=y)
	{
		d++;
		string temp;
		f8>>temp;
		tem[l]=temp;
		l++;
	}
	system("cls");
	cout.setf(ios::left,ios::adjustfield);
	cout<<endl<<endl<<"     NAME :"<<tem[0];
	cout<<"                  FATHER NAME :"<<tem[1];
	cout<<endl<<endl<<"     Ph_no:"<<tem[2];
	cout<<"                   ADDRESS:"<<tem[3];
	cout<<endl<<endl<<"     Alloted seat Number:"<<tem[4];
	cout<<endl<<endl<<endl<<"\n            Total amount DUE : Rs "<<tem[5]<<"|-"<<endl<<endl
	<<"                                                             student sign";
   	cout<<"Enter any key to retun back to menu :";
	getch();
	return 1;

}
int student_login::complaints()
{
	char ch;
	system("cls");
	ofstream fin9;
	fin9.open("complaintbox.cpp",ios::app);
	fin9<<endl;
	string mystr;
   	getline (cin, mystr);
  	cout << "Enter the Complaint :";
  	getline (cin, mystr);
  	fin9<<mystr;
  	cout<<"\n\n\nEnter any key to retun back to menu :";
	getch();
	return 1;
}
int student_login::contactdetails()
{
	system("cls");
	cout<<"\n\n\n   Dr. B.Sreenivasa Reddy,\n   Associate Professor,\n   Dept. of Physics,"
	<<"\n   Room no:K-201,"<<"\n   CBIT,HYD,TELANGANA";
	cout<<"\n   Phone no: 9832333393";
	cout<<"\n\n\n\nEnter any key to retun back to menu :";
	getch();
	return 1;
}



// member functions definitions of reistor_now class
int register_now::instructionsform()
{
	system("cls");
	cout<<"\n          ";
	char b[]="Read the following Instructions\n";
	int x=strlen(b);
	for(int i=0;i<x;i++)
	{
		Sleep(25);
		cout<<b[i];
	}
	char ch;
	char a;
	ifstream ins1;
	ins1.open("instructions.txt",ios::in);
		while(ins1)
		{
			ins1.get(ch);
			cout<<ch;
		}
	cout<<"To accept the above instructions press Y : ";
	cin>>a;
		if(a == 'y' || a == 'Y')
		{
			registration_form();
		}
	 	else
		{
			system("cls");
			cout<<"\n\n\n\n\n               sorry,YOU ENTERED A WRONG CHOICE.....";
			Sleep(1000);
			system("cls");
		}
}
int register_now::registration_form()
{
	string password;
	char pwd[5];
	int i=0;
	system("cls");
	a++;
	fstream fil5;
	fil5.open("login.txt",ios::out|ios::app);
	cout<<"              \n";
	char b[]="REGISTRATION FORM\n";
	int x=strlen(b);
	for(int i=0;i<x;i++)
	{
		Sleep(25);
		cout<<b[i];
	}
	cout<<endl<<endl<<setw(5)<<"NAME :";
	cin>>name[0];
	cout<<setw(40)<<"FATHER NAME :";
	cin>>name[1];
	cout<<endl<<setw(5)<<"Ph_no:";
	cin>>name[2];
	cout<<setw(35)<<"ADDRESS:";
	cin>>name[3];
	cout<<endl<<setw(5)<<"Select seat Number:"<<endl;
	int count=1;
	for(int i=0;i<10;i++)
	{
		for(int j=0;j<5;j++)
		{
			if(j==3)
			{
			cout<<"   ";
			}cout<<setw(4)<<count<<"  ";
			count++;
		}
		cout<<endl;
	}
	cout<<" ";
	for(int i=51;i<=60;i++)
	{
		cout<<setw(3)<<i;
	}
	string user4;
	cin>>name[4];
	cout<<"\n staff or student: ";
	cin>>user4;
	if(user4=="student"||"STUDENT")
	{
	cout<<endl<<endl<<"Your username :";
	cout<<"CBIT"<<a;
	cout<<endl<<"PASSWORD :";
	while(i<4)
	{
		pwd[i]=getch();
		putchar('*');
		++i;
	}
	password=pwd;
	fil5<<"CBIT"<<a;
	fil5<<password<<"\n";
	name[5]="17000";
	cout<<name[5];
	fil5.close();
	fstream fil2;
	fil2.open("list_of_students",ios::in | ios::out | ios::app);
	fil2.seekg(74);
	fil2<<"CBIT"<<a<<"          ";
	//fil2.setf(ios::left,ios::adjustfield);
	for(int i=0;i<6;i++)
	{
	fil2.setf(ios::left,ios::adjustfield);
	fil2<<setw(20)<<name[i];
	count++;
	}
	fil2<<endl;
	Sleep(500);
}
	else
	{
		if(user4=="staff"||"STAFF")
		{
				cout<<endl<<endl<<"Your username :";
	cout<<"STAF"<<a;
	cout<<endl<<"PASSWORD :";
	while(i<4)
	{
		pwd[i]=getch();
		putchar('*');
		++i;
	}
	password=pwd;
	fil5<<"STAF"<<a;
	fil5<<password<<"\n";
	name[5]="17000";
	cout<<name[5];
	fil5.close();
	fstream fil2;
	fil2.open("list_of_students",ios::in | ios::out | ios::app);
	fil2.seekg(74);
	fil2<<"STAF"<<a<<"          ";
	//fil2.setf(ios::left,ios::adjustfield);
	for(int i=0;i<6;i++)
	{
	fil2.setf(ios::left,ios::adjustfield);
	fil2<<setw(20)<<name[i];
	count++;
	}
	fil2<<endl;
	Sleep(500);



		}
	}















	confirmform();
}
int register_now::confirmform()
{
	char ch;
	system("cls");
	char sentzz[]="          ***************CONFIRM FORM*****************";
	int x;              //special dialogue
	int size;
	size=strlen(sentzz);
    for(x=0;x<size;x++)
    {
        Sleep(50);
        cout<<sentzz[x];
    }
    cout.setf(ios::left,ios::adjustfield);
	cout<<endl<<endl<<"     NAME :"<<name[0];
	cout<<"                  FATHER NAME :"<<name[1];
	cout<<endl<<endl<<"     Ph_no:"<<name[2];
	cout<<"                   ADDRESS:"<<name[3];
	cout<<endl<<endl<<"     Alloted seat Number:"<<name[4];
	//cout<<endl<<endl<<"     Your username :"<<"CBIT"<<a;
	cout<<endl<<endl<<endl<<"            Total amount to be paid : Rs 17,000|- on or before 5th july"<<endl
	<<endl<<endl<<"                                                              student sign";
   /*fil2.seekg(0,ios::end);
    int b=fil2.tellg();
    fil2.seekg(-100,ios::end);
    while(fil2)
    {
    	int a=fil2.tellg();
    	cout<<"NAME:";
		if(a!=b)
    	{
			fil2.get(ch);
    		cout<<ch;
    	}*/
    	int a;
    	Sleep(400);
    	cout<<endl<<endl<<"    Enter any key to return back to main menu :";
    	getch();
    	return 1;
	}
int register_now::routes()
{
	char ch;
	system("cls");
	fstream fil4;
	fil4.open("ROUTES.cpp",ios::in);
	while(fil4)
		{
			fil4.get(ch);
			cout<<ch;
		}
}
int register_now::notice()
{
	system("cls");
	char ch;
	ifstream f2;
	f2.open("program.txt",ios::in );
		while(f2)
		{
			f2.get(ch);
			cout<<ch;
		}
	cout<<"\n\n\n Enter any to return back to menu :";
	getch();
	return 1;
}

int main() //functioncall1353
{
	char ch;
	system("COLOR 0F");
	while(1)
	{
		system("cls");
		cout<<endl<<endl;
		fstream f2;
		f2.open("sysmbol.txt",ios::in);
		while(f2)
		{
			f2.get(ch);
			cout<<ch;
		}
	Sleep(10);
	system("COLOR 0");
		char a[]="                \xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb STUDENT TRANSPORT MGMT \xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb\xdb";
		int size;
		size=strlen(a);
		for(int i=0;i<size;i++)
		{
			Sleep(25);
			cout<<a[i];
		}
		int c=1;
		cout<<endl<<endl;
		Sleep(0);
		cout<<"\n                    \t\t1.REGISTER NOW \n                    \t\t2.STAFF LOGIN \n                    \t\t3.STUDENT LOGIN \n"
		<<"                    \t\t4.NOTICES";
	for(int i=0;i<1;i++)
    {
    	int x = 16;
    	int y = 10;
    	for (y=4;y<13;y++)
   		{
    	  gotoXY(x,y);
    	  cout << "\xdb";
    	  Sleep(100);
    	 // gotoXY(x,y);
		 // cout << "                                                     ";
  		}
  		y=13;
  		for (x=16;x<63;x++)
   		{
    	  gotoXY(x,y);
    	  cout << "\xdb";
    	  Sleep(20);
    	 // gotoXY(x,y);
		 // cout << "                                                     ";
  		}
  		for (y=4;y<14;y++)
   		{
    	  gotoXY(x,y);
    	  cout << "\xdb";
    	  Sleep(100);
    	 // gotoXY(x,y);
		 // cout << "                                                     ";
  		}
}
	for(int i=0;i<1;i++)
    {
    	int x = 1;
    	int y = 15;
    	for (x=40;x>1;x--)
   		{
    	  gotoXY(x,y);
    	  cout << "BROUGHT TO YOU BY PIES";
    	  Sleep(100);
    	  gotoXY(x,y);
		  cout << "                                                         ";
		     cout<<"                                            ";
  		}
  		cout <<endl<<"       Created By itsourcecode.com"<<endl;
	}
   register_now r1;
   staff_login s1;
   student_login s2;
   int ch;
	cout<<"\nSelect Your Option :";
	cin>>ch;
	fstream f1;
	switch(ch)
	{
		case 1:system("COLOR 0F");
				r1.instructionsform();
				break;
		case 2:system("COLOR 0F");
				s1.login();
				break;
		case 3:system("COLOR 0F");
				s2.login();
				break;
		case 4:system("COLOR 0F");
				r1.notice();
				break;
		default:cout<<"ssssss";
				break;
	}
	}
	getch();
	return 0;
}

void gotoXY(int x, int y)
{
CursorPosition.X = x; // Locates column
CursorPosition.Y = y; // Locates Row
SetConsoleCursorPosition(console,CursorPosition); // Sets position for next thing to be printed
}
/*void WaitKey()cp
{
   while (_kbhit()) _getch(); // Empty the input buffer
   _getch(); // Wait for a key 1353fn
   while (_kbhit()) _getch(); // Empty the input buffer (some keys sends two messages)
}*/
