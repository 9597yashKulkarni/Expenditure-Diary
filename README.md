# Expenditure-Diary
#include<iostream>
using namespace std;
#include<string.h>
#include<fstream>
#include<stdlib.h>

class Expen_diary
{
public:
	char date[11];
	//Description of expenditure
	int ex[20];
	int expMonth[31];
	int totalDay=0;
	int totalMonth=0;
	float accBalAtStart;
	float accBalAtEnd;
	int amtRemoved;

	char yes[3]="y";
	int i=0;
	int cnt=0;

	ofstream o;
	ifstream in;

	void insert();
	void display();
	void calculate();

};


void Expen_diary::insert()
{
	char ch[2];
	string desExp;
	cout<<"\nInsert date dd/mm/yyyy";
	cin>>date;
	o.open("Expenditure_diary.txt",ios::app);
	o<<"\n\nDate :";
	o<<date;

	do
	{
		cout<<"\nInsert description of expenditure:";
		getline(cin,desExp);
		cout<<desExp;
		o<<desExp;

		cout<<"\nEnter money spent";
		cin>>ex[i];
		o<<ex[i];

		cnt++;
		i++;

	    cout<<"\nDo you want to continue for today 'y' or 'n'";
		cin>>ch;

	}while(strcmp(ch,yes));

	o.close();
}

void Expen_diary::calculate()
{
	for(i=1;i<=cnt;i++)
	{
		totalDay=totalDay+ex[i];
	}
	o<<"Total expenditure of the day is :"<<totalDay;
}

void Expen_diary::display()
{
	cout<<"Total expenditure of the day is :"<<totalDay;
}

int main()
{
	Expen_diary z;
	int n;
	do
	{
		cout<<"\n1.Insert expenditure for today.";
		cout<<"\n2.Display total";
		cout<<"\n3.Exit";
		cout<<"\nEnter your choice";
		cin>>n;
		switch(n)
		{
		case 1:
				z.insert();
				z.calculate();
				break;
		case 2:
				z.display();
				break;
		case 3:
				cout<<"\nThank you";
				exit(0);
				break;
		}
	}while(n<=4);
	getchar();
	return  0;
}
