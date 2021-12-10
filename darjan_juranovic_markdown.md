# Markdown vježba
Ovo je dokument 📝 koji prezentira moj  **`c++`** kod 😃
## Program
```cpp
#include <iostream>
using namespace std;
int main()
{
	int broj,suma=0;
	int jedinice,desetice,stotice;
	cout<<"Upisi troznamenkasti broj: ";
	cin>>broj;
	jedinice=broj%10;
	desetice=(broj/10)%10;
	stotice=(broj/100)%100;
	suma= jedinice+desetice+stotice;
	
	if(broj<1000 && broj>99){
	
	cout<<"Upisani broj je troznamenkasti"<<endl;
}	
	else{
	
	cout<<"Upisani broj nije troznamenkasti"<<endl;
}
	cout<<"Suma upisanih brojeva je: "<<suma<<endl;
	return 0;
}
```
### Pokretanje programa
- Preuzmite [DevCpp](https://sourceforge.net/projects/orwelldevcpp/)
- Kreirajte novu datoteku i kopirajte kod unutra
- Prevedite
- Pokrenite
### TODO
Todo lista za nadopunu programa:
- [x] Ispisati poruku za unos broja
- [x] Omogućiti unos broja
- [ ] Provjeriti je li broj troznamenkast
- [ ] Ispisati sumu znamenki broja

[a



