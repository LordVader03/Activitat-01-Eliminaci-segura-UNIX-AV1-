
# Activitat 01: Eliminació segura UNIX (AV1)

*Instructor*: [Jordi Mateo Fornés](http:jordimateofornes.com)

*Course*: [Grau en Tècniques d'Interacció Digital i de Computació](http://www.grauinteraccioicomputacio.udl.cat/ca/index.html)

*University*: University of Lleida - Campus Igualada - Escola Politècnica Superior

*Estudiants*: Álex Pellitero García

## 1 Part pràctica: Desenvolupament rmsf

NAME
rmsf – safe remove files and folders

SYNOPSIS
rmsf file ...

DESCRIPTION
The rmsf utility attempts to move files and folders on the command line to the .trash/ folder located
at the user’s home. This is not an actual remove. Note that the program will create the .trash folder if it
does not exist. If the file’s permissions do not permit writing, and the standard input device is a terminal,
the user is prompted (on the standard error output) for confirmation.

EXIT STATUS
rmsf exits 0 on success, and >0 if an error occurred.

EXAMPLES
The following examples show common usage:
rmsf file1
rmsf file1 dir
rmsf file1 dir/file2 b
rmsf file1 dir/subdir/file2

### Enunciat
La vostra tasca és implementar en C aquesta funcionalitat.

### Resposta
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <dirent.h>
#include <string.h>
#include <sys/stat.h>

int main (String str)
{
	finddir(trash);
	
	if (finddir == true)
	{
		opendir C:\\home\\trash;
	} else
	{
		mkdir trash;
	}
	
	system("move C:\\str C:\\trash");
	
	return 0;
}

boolean finddir (String str)
{
	opendir(C:\\home);
	
	if (getuid(str))
	{
		return true;
	}
	else
	{
		return false;
	}
}

## 2 Part pràctica: Instal·lant la comanda al sistema rmsf

Expliqueu quin és el procediment per instal·lar aquesta commanda al sistema. Volem que un usuari la
pugui utilitzar directament com rmsf.

### Enunciat
Expliqueu els passos realitzats.

### Resposta
Primer introduim la següent comanda:

su root -c "cp rmsf /usr/bin"

En la que s'ha de posar su root per a crear la comanda, -c perque es de tipus c, després usem rmsf perque és el nom de l'arxiu i /usr/bin, perqué es on es troba l'arxiu.

Després ens demanarà la contrasenya i la possem i ens deixarà creada la comanda.

## 3 Part pràctica: Test

### Enunciat
La vostra tasca és prepar un fitxer test.sh que contingui totes les comandes que heu fet anar per testejar
la vostra solució.

### Resposta
cd usr/bin

vi rmsf.c

gcc rmsf.c -g -c rmsf.c -o rmsf

mkdir hola

rmsf hola

## 4 Part pràctica: Automatització amb Make

## Part pràctica: Instal·lar un paquet 

### Enunciat
La vostra tasca és revisar el funcionament dels Makefiles. Heu de preparar un Makefile que sigui
capaç de compilar, executar, testejar amb el fitxer test.sh i instal·lar l’executable al sistema.

### Resposta
rmsf: rmsf.o
	
	gcc -o rmsf rmsf.o
rmsf.o: rmsf.c

	gcc -c rmsf.c
clean:

	del rmsf rmsf.o
install:
	
	su root -c "cp rmsf /usr/bin"
