Sebastian Cojocariu 321CB UPB ACS                       

				                               Operating System Process Schedulers


   Clasa abstracta Processes va fi mostenita de cele 7 clase reprezentand taskurile 
posibile: CheckPrime,NextPrime,Factorial,Fibonacci,Cube,Square,Sqrt.Aceasta clasa contine campurile
weight(in care se va retine weight-ul fiecarui proces),processName(numele procesului ce ne va fi
de ajutor la cautare) si modulo=9973(final).Totodata avem o metoda f abstracta care va fi implementata de fiecare din cele 7 clase mentionate mai sus(din numele lor se intelege ce va returna fiecare),dar si metoda implementata getProcesses care primeste ca parametru un obiect de tipul ProblemData si returneaza un array de processes,facand cast pentru fiecare proces in parte la tipul de task pe care il reprezinta(CheckPrime,NextPrime,etc).
  
   Clasa abstracta SchedulerTasks contine campul processes(de tipul Processes[]),cat si o metoda abstracta getIndexProcess() care va fi implementata in cele 3 clase ce vor mosteni aceasta clasa,anume RandomScheduler,RoundRobinScheduler,WeightedScheduler.Aceasta metoda va realiza,in functie de clasa care o implementeaza:

1)clasa RandomScheduler:metoda va genera aleator un index care sa fie in limitele array-ului de procese.
2)clasa RoundRobinScheduler:va avea un camp int[] frequency care va retine de cate ori a fost ales un proces anume(frequency[i] va retine de cate ori a fost ales pana la acel moment processes[i]).Cu ajutorul metodei test aflam daca se respecta conditia ca intre fiecare proces sa existe maxim 1 diferenta intre numarul de procese rulate de fiecare la acel moment.Astfel,aceasta metoda va returna un index viabil care sa respecte conditia impusa de test().
3)clasa WeightedScheduler:va avea campurile t(timpul la care trebuie sa verificam conditia),int[] cote(de cate ori trebuie sa apara un proces intre k*t si (k+1)*t momente de timp),moment care retine momentul in care se afla metoda.Metoda cmmdc returneaza cmmdc-ul a 2 nr,getCota() completeaza cote[i] si t-ul,iar test() verifica daca exista un proces care a fost folosit de mai mult de cota[index-ul lui](caz in care va returna 0).Metoda getIndexProcess genereaza un index care sa respecte conditia inpusa de test(),iar daca moment=multiplu de t se apeleaza din nou getCota() pentru a reface array-ul de cote[].

   Clasa abstracta CacheTypes contine o lista dublu inlantuita list ,capacitatea listei ,metodele abstracte add(Key key) si getValue(Key key),dar si de metoda getIndex(Key key).Ea va fi mostenita de clasele NoCache,LfuCache,LruCache.

1)clasa NoCache:nu va fi folosita niciodata,dar va implementa metodele abstracte de mai sus. 
2)clasa LruCache:Implementeaza cele 2 metode abstracte,cu mentiunea ca la fiecare getValue,daca cheia exista va aduce nod-ul care o contine la capatul listei(va reactualiza nodul),iar la add(key) ,daca exista,va sterge nodul care o contine si o va crea un nou nod cu cheia respectiva la capatul listei,iar daca nu o contine o va adauga(cu mentiunea ca daca s-a atins capacitatea maxima a cache-ului va sterge primul nod din lista).
3)clasa LfuCache:Implementeaza cele 2 metode abstracte,cu mentiunea ca la fiecare getValue,daca cheia exista va incrementa campul hit al nodului care respecta conditia,iar la add(key) daca va gasi cheia nu va face nimic,iar daca nu o va adauga(cu mentiunea ca daca s-a atins capacitatea maxima a cache-ului va sterge nodul cu cele mai putine hit-uri(accesari)).

 package PooCbTema1.InputOutput contine 4  clase :HomeworkWriter ,HomeworkReader,ProblemData,ProcessStructure. 

 MainClass: clasa de unde se apeleaza main-ul.A se vedea comentariile din interiorul ei. 
