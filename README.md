# proyectoDemoCursoPrework
#include <iostream>
#include <cmath> /// truncar
#include<cstdlib> /// libreria para la funcion rand -> aleatorio y srand
#include<time.h> /// devuelve el valor del tiempo en s del sistema
#include<fstream> /// archivos
using namespace std;
int main(){ /// Este programa simula un cajero automatico
    system("color "); // sirve para cambiar el color (terminal)
    float ah=5000 /ahorros/,redito,mt;
    int pd[8]={30,60,90,120,180,240,300,360}; /// dias
    float pi[8]={1.6,1.8,2.0,2.2,2.4,2.6,2.8,3.0}; /// porcentaje
    int r,pin,pinc,pin1=1234,t1=3/t1=intentos/,ct,usd,/monto depositar/imp,opi,plz,a=0,it=-1;


    string nom[100],nomst[100],tc,ndst,ctadep,vc[100],conf;
    int j=0,mtr,ctt=0,respuesta2=0,respuestac2=0,mdst;
    int tcc=0,/bool/opst;
    int vr=0; string vco[100];
    int rtra=0; /res transferencia 1 o 2/
    cout<<"BIENVENIDA/O"<<endl;
    fstream arch; // creo al archivo
    srand(time(0)) ; // genera un valor nuevo (hora) sin esto cada vez salen los mismos numeros aleatorios
    do {
    cout<<"PARA REALIZAR UNA TRANSACCION CON TARJETA DIGITE 1 "<<endl;
    cout<<"PARA REALIZAR UNA TRANSACCION SIN TARJETA DIGITE 2 "<<endl;
    cin>>r; // LEER 1 || 2
    if (r!=1 && r!=2){
        cout<<"OPCION INEXISTENTE!!!!!"<<endl;
    }
    }while (r!=1 && r!=2);
    switch (r){
case 1 :
    cout<<"TRANSACCION CON TARJETA"<<endl;
    do{
    cout<<"INGRESE SU PIN (1234)"<<endl; // https://youtu.be/JHfhBjXxE8A
    cin>>pin;
    if (pin!=pin1){
        t1--; // contador intentos (MÁX 3)
        cout<<"# DE INTENTOS RESTANTES: "<<t1<<endl;
        cout<<" t1 : "<<t1<<endl ;}
    }while (t1>0 && pin!=pin1) ;
    do {
    if (pin==pin1){
    cout<<"******************"<<endl;
    cout<<"                    MENU"<<endl;
    cout<<"SELECCIONE UNA OPCION:"<<endl;
    cout<<"1. EXTRACCION"<<endl;
    cout<<"2. DEPOSITOS"<<endl;
    cout<<"3. CAMBIO DE PIN"<<endl; // ph funcion aleatorio
    cout<<"4. INVERSIONES"<<endl;
    cout<<"5. TRANSFERENCIA"<<endl; // talvez otra opcion de servicios adicionales con V M o R
    cout<<"6. PRESIONE CUALQUIER NUMERO ADICIONAL PARA SALIR"<<endl;
    cout<<"******************"<<endl;
    cin>>ct ; // ct = Con Tarjeta
    switch (ct){
    case 1:
         cout<<"1. EXTRACCION"<<endl;
         do{
         cout<<"ELIJA EL IMPORTE QUE VA A RETIRAR (RECUERDE QUE DEBE SER MULTIPLO DE 100)"<<endl;
         cin>>imp;
         if (imp%100!=0){
         cout<<"EL IMPORTE DEBE SER MULTIPLO DE 100"<<endl;}
         }while (imp%100!=0); // mientras no sea multiplo de 100
         if ( imp<=0 || imp>ah ){ //DEBE SER MULTIPLO DE 100 /// es && porque imp%100!=0 debe cumplirse para que ingrese al si mientras que en los otros es || ya que puede cumplirse que seea menor a cero o amyor a los fondos
            cout<<"!!!!! REVISE EL MONTO A RETIRAR INGRESADO !!!!!"<<endl;
         }else{ //imp%100==0
             ah=ah-imp ; // actualizar los fondos
         cout<<"\n--------------RETIRE SU DINERO--------------\n"<<endl;
         }
         break;



    case 2:
         cout<<"2. DEPOSITOS"<<endl;
         cout<<"INGRESE EL MONTO A DEPOSITAR"<<endl;
         cin>>usd;
         ah=ah+usd ;
         cout<<"TRANSACCION COMPLETADA"<<endl;
         cout<<"SU SALDO ES DE: "<<ah<<endl;
         break;

    case 3: cout<<"3. CAMBIO DE PIN"<<endl;

    while (pinc!=pin) { //ingresa pinc = 0 por lo que si cumple
         do{
         cout<<"INGRESE EL PIN ACTUAL"<<endl;
         cin>>pinc;
         }while(pinc!=pin1); // control pin actual correcto
         do{ // control pin nuevo correcto
            pin=rand()%10000+1982 ; // PIN ALEATORIO
            cout<<"SU NUEVO PIN ES "<<pin<<endl;
            cout<<"PARA CONFIRMAR INGRESE EL NUEVO PIN"<<endl;
            cin>>pinc; } while (pin!=pinc);
       }
       pin1=pin;
         break;

    case 4:
    cout<<"4. INVERSIONES"<<endl;
            cout<<"1. POLIZA"<<endl;
            cout<<"RECORDATORIO: SU SALDO ACTUAL ES: "<<ah<<" usd"<<endl;
            do { // control plazo de dias valido 30,60 ...etc
            do { // control valor en el intervalo valido positivo y dentro del margen de la cuenta (ah)
             cout<<"INGRESE EL MONTO QUE VA A INVERTIR"<<endl;
             cin>>mt; //monto
            }while (mt<0 || mt>ah);
             cout<<"INGRESE EL NUMERO DE DIAS QUE VA A INVERTIR (30,60,90,120,180,240,300,360)"<<endl;
             cin>>plz; /// https://www.pichincha.com/portal/simuladores/simulador-de-inversiones
            }while ( plz!=30 && plz!=60 && plz!=90 && plz!=120 && plz!=180 && plz!=240 && plz!=300 && plz!=360  ); //MÍN 31 y dentro del saldo

         do{
                it++; // contador para recorrer el vector
            if (plz==pd[it]){ // comparar si coincide el valor ingresado
                a=it ; // ponerle el valor posicional que es el mismo en dias y procentaje
            }
        }while(plz!=pd[it]);
            redito=mt*pd[a]*pi[a]/(100*360); // calculo de la inversion
            ah=ah+redito; // actualizar el saldo
            cout<<"El resultado de su inversion seria: "<<redito<<" USD"<<endl;
            cout<<"Sus ganancias totales serian de: "<<redito+mt<<" USD"<<endl;
            cout<<"Su saldo seria de: "<<ah<<" USD"<<endl;

         break;
    case 5:
        cout<<"5. TRANSFERENCIA"<<endl;

     arch.open("nombres.txt",ios::in);
     do{
     cout<<"Ingrese el titular de la cuenta"<<endl;
     cin>>tc;
       while(!arch.eof()){
          getline(arch,nom[j]);
          j++;
       }
     tcc=0; // se reinicia el valor
     for (int i=0;i<=j;i++){ // solo lee una vez !arch.eof()
        if (nom[i]!=""){ // imprima solo los datos que no son vacios +1
        cout<<"Titular: "<<nom[i]<<endl;}
        if (tc==nom[i]){
            tcc=1;
        }
     }


     if (tcc==1){ //usuario existente
            do{
        cout<<"¿CUAL ES EL MONTO QUE DESEA TRANSFERIR?"<<endl;
        cin>>mtr;
        }while (mtr<=0 || mt>ah);
        ah=ah-mtr; // actualiza balance
        ctt++; // contador transferencia
        cout<<"Saldo actual: "<<ah<<" usd"<<endl;
     }else{
         cout<<"Usuario inexistente en nuestra base de datos :("<<endl;
         }
              cout<<"PARA REALIZAR OTRA TRANSFERENCIA DIGITE 1 CASO CONTRARIO DIGITE 2"<<endl;
              cin>>rtra;
              }while (rtra==1);
     arch.close();

         break;
    default :
        cout<<"GRACIAS POR USAR NUESTROS SERVICIOS :D"<<endl;
        break;  }
    }
    }while ( ct==1 || ct==2 || ct==3 || ct==4 || ct==5 ); // control intentos pin
    break;

//**************************************//
                                         case 2 :   // CASE 2 GENERAL SIN TARJETA
//**************************************//
    cout<<"TRANSACCION SIN TARJETA"<<endl;
    do{
    cout<<"INGRESE SU PIN (1234)"<<endl; // https://youtu.be/JHfhBjXxE8A
    cin>>pin;
    if (pin!=pin1){
        t1--; // contador intentos (MÁX 3)
        cout<<"# DE INTENTOS RESTANTES: "<<t1<<endl;
        cout<<" t1 : "<<t1<<endl ;}
    }while (t1>0 && pin!=pin1) ;

    if (pin==pin1){
    do{ // bucle menu general sin tarjeta
    do{
    cout<<"SELECCIONE UNA OPCION"<<endl;
    cout<<"1. EXTRACCION"<<endl;
    cout<<"2. DEPOSITOS"<<endl;
    cout<<"3. SALIR"<<endl;
    cin>>opst;
    }while (opst!=1 && opst!=2 && opst!=3);
    switch (opst){
        case 1: cout<<"1. EXTRACCION"<<endl;
        arch.open("codes.txt",ios::in); // leer el  archivo codes
        j=0;
        while(!arch.eof()){
           getline(arch,vco[j]);
           j++;
        }
     for (int i=0;i<=j;i++){
        if (conf==vco[i]){
            vr=1;
    
           }
        }
        if (vr==1)
        {
            cout<<""<<endl;
        }
    arch.close();

        break;
        case 2: cout<<"2. DEPOSITOS"<<endl;
            arch.open("nombres1.txt",ios::in); // leer el 2do archivo nombres1 !=
    cout<<"Ingrese el nombre a depositar"<<endl;
    cin>>ndst;
    cout<<"Ingrese la cuenta a depositar"<<endl;
    cin>>ctadep;
    j=0; // para no usar otra variable porque es otro menu
    while(!arch.eof()){
          getline(arch,nomst[j]);
          j++;
       }

     for (int i=0;i<=j;i++){
        cout<<"Titular: "<<nomst[i]<<endl;
        if (ndst==nomst[i]){
            respuesta2=i; // true
           }
        }
    arch.close(); // cerrar el 2do archivo

    arch.open("ncuentas.txt",ios::in); // leer el 3er archivo ncuentas !=
    j=0;
    while(!arch.eof()){
          getline(arch,vc[j]);
          j++;
       }

     for (int i=0;i<=j;i++){
        cout<<"Cuenta: "<<vc[i]<<endl;
        if (ctadep==vc[i]){
            respuestac2=i; // true
                }
        }
    arch.close(); // cerrar el 3er archivo

    if (respuesta2==respuestac2){ // coincide el nombre y la cuenta
        cout<<"Ingrese el monto a depositar"<<endl;
        cin>>mdst;
        ah=ah-mdst;
        fstream arch1;
    arch1.open("nuevodeposito.txt",ios::app); // leer el 3er archivo para añadir ncuentas !=
    arch1<<"NOMBRE: "<<nomst[respuesta2]<<" CUENTA: "<<vc[respuesta2]<<" Balance: "<<mdst<<" usd \n";
    arch1.close();
     }else{
     cout<<"USUARIO INEXISTENTE EN NUESTRA BASE DE DATOS :("<<endl;
     }
    break;
        case 3:
            cout<<"GRACIAS POR PREFERIR NUESTROS SERVICIOS :D"<<endl; break;}
      }while (opst!=3);
    } }
    return 0;
}

 /*
    MENU
    1. TRANSACCION CON TARJETA
     1.1. EXTRACCION
     1.2. DEPOSITOS
     1.3. CAMBIO DE PIN
     1.4. CONSULTA DE SALDOS
     1.5. TRANSFERENCIA -> https://youtu.be/9BGHO926TuM
     1.6. SALIR
    2. TRANSACCION SIN TARJETA
     2.1. RETIROS
     2.2. DEPOSITOS
     2.3. CAMBIO DE CLAVE
     2.4. CONSULTA DE SALDOS

    Debe ser un programa práctico que se en la vida real.
Debe ser desarrollado en lenguaje C++
Se debe contemplar lo cubierto en los temas revisados en
 la asignatura de Fundamentos de Programación:
Estructuras de programación (condicionales, selectivas, repetitivas)
Vectores o matrices o Registros
Archivos (Obligatorio)
Sub-programas (Voluntario)
Métodos de ordenamiento (Opcional)

    */
