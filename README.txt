# m3-uf1-exc2
## Exercici 2: Blocs de codi, àmbits de variables, estructures bàsiques de control de fluxe i funcions.

En aquest exercici haureu de respondre les següents preguntes, substituint allà on posi //TODO per la vostra resposta.

Haureu d'utilitzar el jshell per a testejar tot el codi relacionat amb cada pregunta, i al final de l'exercici haureu d'incloure en aquest repositori els fitxers _history_ i _snippets_ (seguint el patró de noms establert a l'exercici 0) corresponents a aquest exercici, **directament al directori arrel del repositori**.

### Criteris de qualificació:
* Si no s'incorporen els fitxers _history_ i _snippets_ amb els seus continguts que demostrin que l'alumne ha treballat en les respostes a cadascuna de les preguntes, la qualificació serà de 0.
* Cada pregunta val dos punts, i la seva qualificació podrà ser de 0, 1 o 2, depenent de si la resposta és errònia o molt poc encertada (0), si és parcialment correcte (0.5) o de si és totalment correcte (1).
* Hi ha 5 preguntes, i la qualificació mínima per a superar aquest exercici és de 5/10.
* S'avaluarà la correctesa en la resposta, així com la seva **claredat** (que no presenti ambigüitats).
* Tot i que l'enunciat està redactat en català, l'alumne pot respondre, a banda de en català, en anglès o en espanyol. Faltes d'ortografia en el redactat penalitzarà la nota.

### Preguntes

#### Pregunta 1 - Números primers

Escriu una funció, la signatura de la qual serà

```
void isPrime(int n);
```

que imprimeixi _true_ si n és un número primer positiu, o _false_ si n és un número no primer o bé és 0, o bé és un enter negatiu.

Escriu aquesta funció a continuació:

void isPrime(int n){
if(n>=2){
 if(n==2){
 	print("True");
 }else{
  for(int i=2;i<n;i++){
	if(n%n==0&&n%1==0&&n%i==0){
		print(" FALSE ");
	}
    }
	if(n%n==0&&n%1==0){
	print(" true ");
	}
  }
}else{
  print(" false ");
}
}


Ara, escriu una altra funció, que tindrà per signatura:

```
void findPrimes(int a, int b);
```
que donat un rang [a,b] de números enters, imprimeixi per pantalla aquells números que siguin primers i positius.
Aquesta funció hauria de fer ús de la funció anterior _isPrime(int n)_, de la qual n'hauràs de fer un _override_ per 
a adaptar-la als requeriments de la funció _findPrimes_ (és a dir, la primera funció imprimeix _true_ o _false_, 
mentre que la segona funció imprimeix els números en sí mateixos però només si compleixen la condició -que sigui 
primer i positiu-).

-(overriding de la funció _isPrime_):
@Override
void isPrime(int n){
if(n>=2){
 if(n==2){
 	print("True");
 }else{
  for(int i=2;i<n;i++){
	if(n%n==0&&n%1==0&&n%i==0){
		print(" FALSE ");
	}
    }
	if(n%n==0&&n%1==0){
	print("True");
	}
  }
}else{
  print("El numero "+n+" no es valid");
}
}

- funció _findPrimes_):
void findPrimes(int a, int b){
if(a>=2){
      while(a<b){
	  if(isPrime(a)=="True"){
		println(a);
		a++;
	  }
	 }
 }else{
	print("Aquest numero no es valid");
 }
}

#### Pregunta 2 - Màxim comú divisor

En aquest exercici has de crear una funció que retorni el GCD (_Greatest Common Divisor_ - o Màxim Comú Divisor) de dos enters
positius donats:

```
int gcd(int n, int m);
```
Per a resoldre aquest problema heu d'implementar amb Java l'**algorisme d'Euclides**.
Trobareu informació i exemples sobre aquest algorisme a:

https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic/a/the-euclidean-algorithm

Escriu a continuació la funció _gcd_:

int gcd(int n,int m){
int dividendo=m;
int divisor=n;
int residuo=m%n;
int cociente=m/n;
if(n<m||n>m){
  if(m%n!=0||n%m!=0){
    while(residuo>0){
   	  dividendo=divisor;
	  divisor=residuo;
	  residuo=dividendo%divisor;
	  cociente=dividendo/divisor;
	 }
	 }else{
	  return divisor;
	 }
}
return divisor;
}

#### Pregunta 3 - Recursivitat

Escriu una funció, amb la següent signatura, que calculi i retorni el factorial d'un número enter positiu donat:

```
int factorial(int n);
```

Aquesta funció ha de retornar -1 sempre que el valor del paràmetre n sigui un número negatiu.

Aquesta funció ha de fer ús del concepte de recursivitat.

Escriu el cos de la funció a continuació:

int factorial(int n){
if(n<0){      //condició que retorna -1 si n es un numero negatiu.
 return -1;
}
if(n==0){      //condició que retorna 1 quan el procés de recursitat de n arribi al 0.
 return 1;
}else{     //condició que executa el procès de recursivitat el qual consisteix en que utilitzarem el métode "factorial" per fer factorial de n
 return n*(factorial(n-1));     //cridem a la funció "factorial" per executar-lo amb el valor de n-1 y multiplicat pel valor de "n", és un cicle que es repeteix fins que n sigui igual a 0
}
}



#### Pregunta 4

4.1- Si volem consultar el número d'iteracions que un bucle ha fet quan ha acabat, quina estructura de control de fluxe utilitzarem,
un _while_ o un _for_? Per què?

En el cas de voler saber el número de vegades que es produeix la execució d'un procès hem d'utilitzar el bucle FOR, ja que el bucle WHILE 
no coneix el numero de repeticions perquè comença amb la verificació d'una condició(la qual pot ser vertadera o falsa), en canvi el bucle 
FOR segueix una estructura(inicialització, expressió booleana, actualització(increment o decrement)) lo qual cosa permet tindre en compte
continuament quins passos haurá de realitzar.

Exemple:
Una funció en la qual s'introdueix una array i ha de retornar els valors de la array, en el cas de fer-lo amb un bucle FOR, la 
estructura que segueix ens permet encapsular la variable "i", que es declara dins dels bucle FOR i condicionar-la de forma que aquesta sigui
menor que la longitud de la array que s'introduieixi, i mentre això es cumpli es sumará mes 1 la i, de forma que al final podem saber quants 
valors hi han dins la array, podem fer us d'un derivat del bucle FOR que es el bucle FOREACH.

int getArray(int[]a){
int arr=0;
 for(int i=0;i<a.length;i++){
  arr=i;
}
return arr;
}

Si tenim en compte aquest exemple, podem saber quantes voltes ha fet el bucle(parteix desde la posició 0 fins la posició 3, llavors ha 
fet tres voltes).



4.3- Explica per què serveix una variable anomenada _found_ de tipus booleà, que se sol utilitzar quan programem bucles.
Posa almenys un exemple original teu i que no haguem vist a classe.

El booleà s'utilitza generalment per dir si alguna cosa es vertadera o si es falsa(un dade es contraposa a un altre),
amb aquest es pot fer us de diferents operadors, els quals serveixen per especificar una condició, una d'ordre,
operadors lógics, etc.


Si anomenem "found" a una variable de tipus booleà, llavors aquesta variable tindrà la finalitat d'indicar si un dade ha sigut trobat o no
i es pot fer us d'aquesta segons convengui.

Exemple:

jshell> boolean numeroEncontar(int[]arr,int number){
   ...> boolean founded=false;
   ...>  for(int i=0;i<arr.length;i++){
   ...>   if(arr[i]==number){
   ...>    founded=true;
   ...>    print("numero trobat a la posicio "+i +"  ");
   ...>    }
   ...>   }
   ...> return founded;
   ...> }



4.4- Explica amb exemples la diferència entre fer un _overriding_ de funcions o fer-ne un _overloading_.

Segons el que he investigat, el Overriding en java és la capacitat d'un mètode (conjunt d'instruccions) que pot canviar la seva
comportament per adaptar-se a un altre métode que té el seu mateix nom, que principalment pertany a una classe base (és a dir a una classe 
principal que ja ha estat declara abans).

Exemple:
void listaCompra(){//clase padre(o primaria)
 print("Zanahoria");
 print("Patatas");
}
void listaCompra(){//clase hijo(o secundaria)
 print("Manzana");
 print("Naranja");
}
//Comparteixen mateix nom però diferent contingut



L'overloading passa quan dos o més mètodes en una classe tenen el mateix nom de mètode però diferents paràmetres.

Exemple:
void marca(int marca){
	//contingut 
}

void marca(String[]maques){
	//contingut 
}


#### Pregunta 5

Escriu una funció que, donada una seqüència de números enters entre el 65 i el 90 (inclosos), t'imprimeixi per pantalla la seqüència 
corresponent de caràcters segons la codificació estàndard Unicode.

La signatura d'aquesta funció serà:

```
void printChars(int a, int ... b);
```
Aquesta funció ha d'imprimir el següent missatge d'error si algun dels enters està fora del rang [65,90]:

```
Error: Enter fora del rang [65,90]
```

Escriu la funció a continuació:

#####FUNCIÓ SENSE _foreach_:
jshell> void printChars(int a, int b){
   ...> if(a<65||b<65||a>90||b>90){
   ...>  print("Error: Enter fora del rang [65-90]");
   ...> }else{
   ...> for(int i=a;i<=b;i++){
   ...>  print((char)i+" ");
   ...> }
   ...> }
   ...> }
##################

#######FUNCIÓ AMB FOREACH
funció amb _foreach_:
jshell> void printChars(int a,int... b){
   ...> int[]values={65,66,67,68,69,80,81,82,83,84,85,86,87,88,89,90};
   ...>  for(int i:b){
   ...>  print((char)i);
   ...>   }
   ...>  }
###########################

**Hints**:
Per a recórrer tots els enters introduits com a paràmetres, has d'usar una variant del _for_ anomenada _foreach_, de la qual 
teniu un exemple a continuació:
```
for (int i: b) print(i);
```
(essent b el paràmetre varargs). Nota: tot i que aquesta variant es diu _foreach_, se segueix utlitzant la paraula clau _for_.

Per a imprimir una cadena de text, heu d'escriure el literal entre cometes dobles. Exemple:
```
println("Cadena de texte");
```



             

