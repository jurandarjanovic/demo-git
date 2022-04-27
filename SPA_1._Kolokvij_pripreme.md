<h1 align="center"> 1.KOLOKVIJ SPA </h1>



<h3 align="center">
    POLINOMI
</h3>



#### Zadatak 1 ####

```cpp
#include <iostream>
using namespace std;
#include "polinomATP.h"
//1. Napišite program koji sadrži funkciju void ispis(polinom p) koja ispisuje polinom u sređenom obliku (ne ispisuje koeficijente koji su 0). Primjer ispisa: 2x^4-3x-3.1x^2-x^1+5. U main funkciji kreirajte jedan polinom četvrtog stupnja i demostrirajte na njemu rad funkcije.


void ispis(polinom p){
	for(int i=Degree(p); i >= 0; i--){
		if(Coef(p, i)==0){
			continue;
		}
		else{
			if(i > 0){
				cout<<Coef(p, i)<<"x^"<<i<<" + ";
			}
			else{
				cout<<Coef(p, i);
			}
		}
	}
	cout<<endl;
}


int main(){
	polinom Poli;
	Zero(&Poli);
	Attach(&Poli,0,3);
	Attach(&Poli,1,5);
	Attach(&Poli,2,0);
	Attach(&Poli,3,4);
	Attach(&Poli,4,6);
	ispis(Poli);
	
	system("PAUSE");
}
```



#### Zadatak 2

```cpp
#include <iostream>
using namespace std;
#include "polinomATP.h"
//2. Napišite funkciju int neg_koef(polinom p) koja uzima polinom p i vraća broj njegovih negativnih koeficijenata.


int neg_koef(polinom p){
	int count = 0;
	for(int i = 0; i<=Degree(p); i++){
		if(Coef(p, i) < 0) count++;
	}
	
	return count;
}


int main(){
	polinom Poli;
	Zero(&Poli);
	Attach(&Poli,0,3);
	Attach(&Poli,1,-2);
	Attach(&Poli,2,-1);
	Attach(&Poli,3,-4);
	Attach(&Poli,4,6);
	cout<<"Nas polinom ima "<<neg_koef(Poli)<<" negativnih koeficijenata."<<endl;
	
	system("PAUSE");
}
```



#### Zadatak 3 ####

```cpp
#include <iostream>
using namespace std;
#include "polinomATP.h"
//3. Napišite funkciju bool sparse(polinom p) koja uzima polinom p i vraća true ako je 50% ili više koeficijenata polinoma p jednako 0.


bool sparse(polinom p){
	
	int count = 0;
	
	for(int i=0; i<=Degree(p); i++){
		if(Coef(p, i) == 0) count++;
	}
	
	if(((float)(Degree(p)+1)/2) > count) return false;
	else return true;
}


int main(){
	polinom Poli;
	Zero(&Poli);
	Attach(&Poli,0,3);
	Attach(&Poli,1,1);
	Attach(&Poli,2,0);
	Attach(&Poli,3,-4);
	Attach(&Poli,4,6);
	cout<<sparse(Poli)<<endl;
	
	system("PAUSE");
}
```



#### Zadatak 4 ####

```cpp
void ispis(polinom p){  //4. U header datoteku dopišite funkciju ispisa koja ispisuje sve ne-nul koeficijente i pripadne potencije x^i, počevši od slobodnog člana. Pri tome ispisujte elemente polja values, ali ne pomoću funkcije Coef().
	for(int i=p.en-1; i >= 0; i--){
		if((p.values[i])==0){
			continue;
		}
		else{
			if(i > 0){
				cout<<(p.values[i])<<"x^"<<i<<" + ";
			}
			else{
				cout<<(p.values[i]);
			}
		}
	}
	cout<<endl;
}
```



#### Zadatak 5 ####

```cpp
void Mult_n(polinom *p, float n){ // 5. U header datoteku dopišite funkciju void Mult_n(polinom *p, float n) koja množi polinom *p brojem n

	for(int i=0; i < ((p->en)-1); i++){
		p->values[i]*= n;
	}
	
	ispis(*p);
}
```





<h3 align='center'> REKURZIJA </h3>



#### Zadatak 1 ####

```cpp
#include <iostream>
using namespace std;
//1. Napišite rekurzivnu funkciju koja računa sumu parnih brojeva od 1 do n.


int parnasuma(int n){

	if(n != 0){
		if(n%2==0){
			return n + parnasuma(n - 1);
			}
		return parnasuma(n - 1);
	}
	else return n;
}


int main(){
	int p;
	cin>>p;
	cout<<parnasuma(p)<<endl;
	
	
	system("PAUSE");
}
```



#### Zadatak 2 ####

```cpp
#include <iostream>
using namespace std;
//2. suma znamenki cijelog broja

int sumaznamenki(int a){
	if(a == 0) return 0;
	cout<<a<<endl;
	return (a % 10 + sumaznamenki(a / 10));
}


int main(){
	int broj;
	cout<<"Unesi broj: ";cin>>broj;
	cout<<sumaznamenki(broj);
	
	system("PAUSE");
}
```



#### Zadatak 3 ####

```cpp
#include <iostream>
using namespace std;

void ispisiTrokut(int n){
	
	if(n > 1) {
		ispisiTrokut(n-1);	
	}
	for(int i=1;i<=n;i++){
		cout << i;
	}
	cout << endl;
	
	
	
}


int main(){
	
	ispisiTrokut(7);
	system("PAUSE");
	return 0;
}
```





<h3 align='center'> VEZANA LISTA </h3>



#### Zadatak 1 ####

```cpp
#include <iostream>
using namespace std;
//1. Kreirajte istu mojalista (1,2). Dodajte element 3 na početak liste te element 4 na kraj liste. Ispišite elemente liste.


typedef int elementtype; 
struct element{
	elementtype value;
	element* next;
};
typedef element* List;

void printL(List Li){
	element *t=Li;
	if(t==NULL) cout<<"Prazna lista!"<<endl;
	while(t!=NULL){
		cout<<t->value<<" -> ";
		t=t->next;
	}
	cout<<endl;
}


int main(){
	List Lista;
	Lista = NULL;
	element *a, *b;
	a = new element;
	b = new element;
	
	a->value=1;
	a->next=b;
	b->value=2;
	b->next=NULL;
	
	Lista = a;
	printL(Lista);
	
	element *c, *d;
	c = new element;
	d = new element;

	c->value=3;
	c->next=a;
	Lista = c;
	
	b->next=d;
	d->value=4;
	d->next=NULL;
	
	printL(Lista);
	
	system("PAUSE");
}
```



#### Zadatak 2 ####

```cpp
#include <iostream>
using namespace std;
//U listu iz zadatka 1. dodajte neki element na: a) drugo mjesto b) treće mjesto. Poslužite se kodom uz prezentaciju (dodavanje elementa u sredinu liste).


typedef int elementtype; 
struct element{
	elementtype value;
	element* next;
};
typedef element* List;

void printL(List Li){
	element *t=Li;
	if(t==NULL) cout<<"Prazna lista!"<<endl;
	while(t!=NULL){
		cout<<t->value<<" -> ";
		t=t->next;
	}
	cout<<endl;
}


int main(){
	List Lista;
	Lista = NULL;
	element *a, *b;
	a = new element;
	b = new element;
	
	a->value=1;
	a->next=b;
	b->value=2;
	b->next=NULL;
	
	Lista = a;
	printL(Lista);
	
	element *c, *d;
	c = new element;
	d = new element;

	c->value=3;
	c->next=a;
	Lista = c;
	
	b->next=d;
	d->value=4;
	d->next=NULL;
	
	printL(Lista);
	
	//novi zadatak 2.
	element *e, *f;
	e = new element;
	f = new element;
	
	e->value=5;
	f->value=6;
	
	f->next=c->next;
	e->next=f;
	c->next=e;
	
	printL(Lista);
	
	system("PAUSE");
}
```





<h3 align='center'> STOG </h3>



#### Zadatak 1 ####

```cpp
#include <iostream>
using namespace std;
#include "ATPStackArray.h"
//1. Napiši funkciju ar_sred(Stack *S) koja vraća aritmetičku sredinu elemenata stoga (nakon izvršenja funkcija stog mora ostati nepromijenjen).


float ar_sred(Stack *S){
	Stack Temp;
	InitS(&Temp);
	float ars = 0;
	int count = 0;
	
	while(!IsEmptyS(*S)){
		PushS(TopS(*S), &Temp);
		PopS(S);
	}
	
	while(!IsEmptyS(Temp)){
		ars += TopS(Temp);
		count++;
		
		PushS(TopS(Temp), S);
		PopS(&Temp);
	}
	
	return ars = ars/count;
}


int main(){
	Stack PAS;
	InitS(&PAS);
	PushS(1, &PAS);
	PushS(4, &PAS);
	PushS(7, &PAS);
	PushS(10, &PAS);
	PushS(13, &PAS);
	PushS(16, &PAS);
	
	cout<<"Aritmeticka sredina je: "<<ar_sred(&PAS)<<endl;
	
	system("PAUSE");
	return 0;
}
```



#### Zadatak 2 ####

```cpp
#include <iostream>
using namespace std;
#include "ATPStackArray.h"
//2. Napiši funkciju ispisi_nepar(Stack *S) koja ispisuje samo neparne elemente stoga (nakon izvršenja funkcija stog mora ostati nepromijenjen).


void ispisi_nepar(Stack *S){
	Stack Temp;
	InitS(&Temp);
	
	while(!IsEmptyS(*S)){
		PushS(TopS(*S), &Temp);
		PopS(S);
	}
	
	while(!IsEmptyS(Temp)){
		if(TopS(Temp)%2!=0){
			cout<<"Negativan clan pronaden: "<<TopS(Temp)<<endl;
		}
		
		PushS(TopS(Temp), S);
		PopS(&Temp);
	}
}


int main(){
	Stack PAS;
	InitS(&PAS);
	PushS(1, &PAS);
	PushS(4, &PAS);
	PushS(7, &PAS);
	PushS(10, &PAS);
	PushS(13, &PAS);
	PushS(16, &PAS);
	
	ispisi_nepar(&PAS);
	
	system("PAUSE");
	return 0;
}
```



#### Zadatak 3 ####

```cpp
#include <iostream>
using namespace std;
#include "ATPStackArray.h"
//3. Napiši funkciju void obrni(Stack *S) koja obrne sadržaj stoga.


void ispisi_nepar(Stack *S){
	Stack Temp;
	InitS(&Temp);
	
	while(!IsEmptyS(*S)){
		PushS(TopS(*S), &Temp);
		PopS(S);
	}
	
	PrintS(Temp);	
}


int main(){
	Stack PAS;
	InitS(&PAS);
	PushS(1, &PAS);
	PushS(4, &PAS);
	PushS(7, &PAS);
	PushS(10, &PAS);
	PushS(13, &PAS);
	PushS(16, &PAS);
	ispisi_nepar(&PAS);
	
	system("PAUSE");
	return 0;
}
```



#### Zadatak 4 ####

```cpp
#include <iostream>
using namespace std;
#include "ATPStackArray.h"
//4. Napiši funkciju zamijeni(elementtype x, elementtype y , Stack *S) koja svaku pojavu podatka x u stogu zamijeni sa y


void zamijeni(elementtype x, elementtype y , Stack *S){
	Stack Temp;
	InitS(&Temp);
	
	while(!IsEmptyS(*S)){
		PushS(TopS(*S), &Temp);
		PopS(S);
	}
	
	while(!IsEmptyS(Temp)){
		if(TopS(Temp)==x){
			PopS(&Temp);
			PushS(y, &Temp);
		}
		
		PushS(TopS(Temp), S);
		PopS(&Temp);
	}
	
	PrintS(*S);
}


int main(){
	Stack PAS;
	InitS(&PAS);
	PushS(1, &PAS);
	PushS(4, &PAS);
	PushS(7, &PAS);
	PushS(10, &PAS);
	PushS(13, &PAS);
	PushS(16, &PAS);
	zamijeni(4, 6, &PAS);
	
	system("PAUSE");
	return 0;
}
```
