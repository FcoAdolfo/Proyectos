# Proyectos

Grupo: Ghost code
Fleury Matias Bautista Nuñez (20-1458)
Rosa Elena Peña (21-0415)
Francisco Adolfo (20-0866)


##################################


from hashlib import new
import os, sys
import time
from tkinter.filedialog import SaveAs

os.system('cls')
def mostrar_menu(opciones):
    print('Seleccione una opción:')
    for clave in sorted(opciones):
        print(f' {clave}) {opciones[clave][0]}')


def leer_opcion(opciones):
    while (a := input('Opción: ')) not in opciones:
        print('Opción incorrecta, vuelva a intentarlo.')
    return a


def ejecutar_opcion(opcion, opciones):
    opciones[opcion][1]()


#Solicitud de prestamo#


def generar_menu(opciones, opcion_salida):
    opcion = None
    while opcion != opcion_salida:
        mostrar_menu(opciones)
        opcion = leer_opcion(opciones)
        ejecutar_opcion(opcion, opciones)
        print()


def menu_principal():
    print('-----------------MENU PRINCIPAL-----------------')
    opciones = {
        '1': ('Validación de Solicitud de Prestamos', accion1),
        '2': ('Salir', salir)
    }

    generar_menu(opciones, '2')


def accion1():
    print('Has elegido la opción 1')
    time.sleep(0.5)
    os.system('cls')
    nombre_de_cliente = str(input('Cual es su nombre?: '))
    direccion_cliente = str(input('Cual es su direccion actual?: '))
    numero_de_cedula = int(input('Cual es el numero de su cedula?: '))
    numero_de_cuenta = int(input('Cual es su numero de cuenta: '))
    edad = float (input ('Ingresar su edad: '))
    monto_solicitado = float (input ('Que monto desea solicitar?: '))
    plazo_de_cuotas = float (input ('A que tiempo desea su prestamo?: '))
    sueldo = float (input ('Cual es su salario mensual?: '))
    print ('Selecciona el valor de nacionalidad.')
    print ('\t1.- dominicano')
    print ('\t2.- otra')
    sys.stdout.write ('\t')
    nacionalidad = 0
    while nacionalidad<1 or nacionalidad>2:
        nacionalidad = int (input (': '))
        if nacionalidad<1 or nacionalidad>2:
            sys.stdout.write ('Valor incorrecto. Ingresalo nuevamente.')
    print ('Alguna vez a estado en sicla por algun prestamo por pagar?.')
    print ('\t1.- Si')
    print ('\t2.- No')
    sys.stdout.write ('\t')
    presenta_morosidades = 0
    while presenta_morosidades<1 or presenta_morosidades>2:
        presenta_morosidades = int (input (': '))
    if presenta_morosidades<1 or presenta_morosidades>2:
        sys.stdout.write ('Valor incorrecto. Ingresalo nuevamente.')
    while True:
        if monto_solicitado>10000 and plazo_de_cuotas>=2 and plazo_de_cuotas<=84 and edad>=19 and edad<=69 and nacionalidad==1 and sueldo>=25000 and presenta_morosidades==2:
            print ('Cumple con los requisitos.')
            monto_maximo=sueldo*10
            tasa_mensual=1.46
            monto_a_pagar=monto_maximo*tasa_mensual
            print ('Nombre de cliente: ' + nombre_de_cliente)
            print ('Cedula del cliente: '+ repr(numero_de_cedula))
            print ('Numero de cuenta: ' + repr(numero_de_cuenta))
            print ('Valor de monto a pagar: ' + repr (monto_a_pagar))
            print ('Valor de monto maximo: ' + repr (monto_maximo))
            print ('Valor de tasa mensual: ' + repr (tasa_mensual))
            with open("file.txt","a") as f:
                f.write ('Nombre de cliente: ' + nombre_de_cliente)
                f.write ('\nCedula del cliente: ' + repr(numero_de_cedula))
                f.write ('\nNumero de cuenta: ' + repr(numero_de_cuenta))
                f.write ('\nValor de monto a pagar: ' + repr (monto_a_pagar))
                f.write ('\nValor de monto maximo: ' + repr (monto_maximo))
                f.write ('\nValor de tasa mensual: ' + repr (tasa_mensual))
                f.write ('----------------------------------------------------')
            time.sleep (10)
            os.system ('cls')

        else:
            print ('No cumple con los requisitos.')
            monto_maximo=0
            tasa_mensual=0
            time.sleep(3)
            os.system('cls')
            break

    print (menu_principal)




def accion2():
    print('Has elegido la opción 2')
    time.sleep(3)
    os.system('cls')


def accion3():
    print('Has elegido la opción 3')
    time.sleep(3)
    os.system('cls')


def salir():
    while True:
        print('Saliendo')
        time.sleep(3)
        os.system('cls')
        break



if __name__ == '__main__':
    menu_principal()










################################################


from manager import Manager
import helpers


class Menu:

    @staticmethod
    def loop():
        while True:

            helpers.clear()

            print("========================")
            print("  BIENVENIDO AL GESTOR  ")
            print("========================")
            print("[1] Listar clientes     ")
            print("[2] Mostrar cliente     ")
            print("[3] Añadir cliente      ")
            print("[4] Modificar cliente   ")
            print("[5] Borrar cliente      ")
            print("[6] Salir               ")
            print("========================")

            option = input("> ")

            helpers.clear()

            if option == '1':
                print("Listando los clientes...\n")
                Manager.show_clients()
            if option == '2':
                print("Mostrando un cliente...\n")
                Manager.find()
            if option == '3':
                print("Añadiendo un cliente...\n")
                Manager.add()
                print("Cliente añadido correctamente\n")
            if option == '4':
                print("Modificando un cliente...\n")
                if Manager.edit():
                    print("Cliente modificado correctamente\n")
            if option == '5':
                print("Borrando un cliente...\n")
                if Manager.delete():
                    print("Cliente borrado correctamente\n")
            if option == '6':
                print("Saliendo...\n")
                break

            input("\nPresiona ENTER para continuar...")




##########################################


#Consulta y registro de clientes#


print "menu Registro\n\n1)-Nuevo\n2)-Mostrar\n3)-Eliminar Registro"

opcion = raw_input("Elige una opcion: ")

if opcion == 1:
	print "Nuevo Registro\n"
    archivo = open("ConsultaRegistroCliente.csv","a")

    nombre = raw_input("Ingrese su nombre: ")
    telefono = raw_input("Ingrese su telefono: ")
    cedula = raw_input("Digite su numero de cedula: ")
    direccion = raw_input("Ingrese su direccion: ")
    correo = raw_input("Ingrese su correo: ")

    print "se han capturado: " + nombre + ", con el tel: " + telefono

    archivo.write(nombre)
    archivo.write(",")
    archivo.write(telefono)
    archivo.write(",")
    archivo.write(cedula)
    archivo.write(",")
    archivo.write(direccion)
    archivo.write(",")
    archivo.write(correo)
    archivo.write(",")
    archivo.write("\n")

    archivo.close()


elif opcion == "2":
	print "Mostrar Registro\n"
    archivo = open("ConsultaRegistroCliente.csv")

    print(archivo.read())

    archivo.close()

elif opcion == "3":
	 archivo = open("ConsultaRegistroCliente.csv" "a")
	 archivo.truncate()

	 print "Registros Eliminados"

	 archivo.close()


   else:
   	   print "Debes de elegir una de las opciones anteriores"





#################################################



Banco



print("06. CALCULAR EL INTERÉS MENSUAL DE 10% DE UN PRÉSTAMO DE $1000.")
monto = 1000
meses = int(input("Ingrese Nro de Meses : "))
intereses = (monto*(meses*0.10))
totalp = monto+intereses
print("Interes    : {:.2f}".format(intereses))
print("Pago Total : ", totalp)
print("06. CALCULAR EL MONTO A PAGAR POR UN PRÉSTAMO")
monto = float(input("Ingrese monto del préstamo : "))
tasa  = int(input("Ingrese tasa de interés : % "))
meses = int(input("Ingrese Nro de meses : "))

interes = monto * ( meses * (tasa / 100))
totalp  = monto + interes
print("Interés Generado : $ {:.2f}".format(interes))
print("Pago Total  : $ {:.2f}".format(totalp))
from reportlab.platypus import SimpleDocTemplate, Table, Paragraph, TableStyle 
from reportlab.lib import colors 
from reportlab.lib.pagesizes import A4 
from reportlab.lib.styles import getSampleStyleSheet 
  
DATA = [ 
    [ "Fecha" , "Nombre", "Subscripcion", "Precio(Rs.)" ], 
    [ 
        "16/11/2020",  
        "Lifetime", 
        "10,999.00/-", 
    ], 
    [ "Sub Total", "", "", "20,9998.00/-"], 
    [ "Descuento", "", "", "-3,000.00/-"], 
    [ "Total", "", "", "17,998.00/-"], 
] 
  
pdf = SimpleDocTemplate( "recibo.pdf" , pagesize = A4 ) 
  
styles = getSampleStyleSheet() 
  
title_style = styles[ "Heading1" ] 
  
title_style.alignment = 1
  
title = Paragraph( "Sistema de banco" , title_style ) 
  
style = TableStyle( 
    [ 
        ( "BOX" ,( 0, 0 ),( -1, -1 ), 1 , colors.black ), 
        ( "GRID" ,( 0, 0 ),( 4 , 4 ), 1 , colors.black ), 
        ( "BACKGROUND" ,( 0, 0 ),( 3, 0 ), colors.gray ), 
        ( "TEXTCOLOR" ,( 0, 0 ),( -1, 0 ), colors.whitesmoke ), 
        ( "ALIGN" ,( 0, 0 ),( -1, -1 ), "CENTER" ), 
        ( "BACKGROUND" ,( 0 , 1 ) ,( -1 , -1 ), colors.beige ), 
    ] 
) 
  
def __init__(self, __dni,__nombre,__apellidos) -> None:
    self.set_dni(__dni)
    self.set_nombre(__nombre)
    self.set_apellidos(__apellidos)

def set_dni(self, dni):
    self.__dni = dni

def get_dni(self):
    return self.__dni

def set_nombre(self, nombre):
    self.__nombre = nombre

def get_nombre(self):
    return self.__nombre

def set_apellidos(self, apellidos):
    self.__apellidos = apellidos

def get_apellidos(self):
    return self.__apellidos

def __eq__(self, otro: object) -> bool:
    if type(self) != type(otro):
        return NotImplemented
    return self.__dni == otro.__dni
	def __init__(self, __concepto, __cantidad) -> None:
    self.__concepto = __concepto
    self.__cantidad = __cantidad

def get_concepto(self):
    return self.__concepto

def get_cantidad(self):
    return self.__cantidad

def __hash__(self) -> int:
    return hash((self.__concepto, self.__cantidad))
	def __init__(self, __numero, __titular, __saldo, __movimientos = None) -> None:
    self.__numero = __numero
    self.set_titular(__titular)
    self.__saldo = __saldo

    if __movimientos is None:
        self.__movimientos = {}
    else:
        self.__movimientos = __movimientos

def set_titular(self, titular):
        self.__titular = titular

def get_titular(self):
        return self.__titular

def get_numero(self):
    return self.__numero

def __hash__(self) -> int:
    return hash(self.__numero)

def get_saldo(self):
    return self.__saldo
