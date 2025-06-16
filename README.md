print("Golden caps")
print("1.entrar")
print("2.comprar gorra")
print("3.registrate")
print("4.productos disponibles")
print("5.realiza tu compra")
print("6.saliendo")


opcion= int(input("selecciona una opcion(1-5)"))

match opcion:
    case 1:
        print("Entrando..")
    case 2:
        print("Elije tu gorra favorita")
    case 3:
        print("registrate")
    case 4:
        print("productos disponibles")
    case 5:
        print("realiza tu compra")
    case 6:
        print("saliendo..")
    case _:
        print("Opcion no valida. Intenta de nuevo.")

gorras={}
def agregar ():
    codigo= input("ingresar el codigo")
    if codigo in gorras:
        print("no la tenemos en existencia")
    else:
        nombre=input()
        cantidad=int(input())
        precio=float(input())

    gorras['codigo']={'nombre':nombre,'cantidad':cantidad,'precio':precio}
    print(f"La gorra{nombre} fue registrada con exito")

cantidad=-1
if cantidad > 0:
    raise Exception("no se permirten numeros negativos.")

while True:
    try:
        cantidad= int(input("Ingrese la cantidad de gorras"))
        if cantidad< 1:
            print("Debe haber al menos una disponible.")
        else:
            break
    except ValueError:
        print("ingrese un numero valido.")

precio=-1
while True:
    try:
        cantidad= float(input("precio de la gorra"))
        if precio < 0:
            print("El precio no puede ser negativo.")
        else:
            break
    except ValueError:
        print("Ingrese un precio valido")

def mostrar_productos():
    if not gorras:
        print("No hay productos registrados.")
    else:
        print("Gorras disponibles:")
        for codigo, datos in gorras.items():
            print(f"Código: {codigo}  Nombre: {datos['nombre']} Cantidad: {datos['cantidad']}  Precio: {datos['precio']}")

def realizar_compra():
    if not gorras:
        print("No hay productos disponibles para comprar.")
        return

    mostrar_productos()
    codigo = input("Ingresa el código de la gorra que deseas comprar: ")
    if codigo not in gorras:
        print("Gorra no encontrada.")
        return

    try:
        cantidad_compra = int(input("¿Cuántas unidades deseas comprar?: "))
        if cantidad_compra < 1:
            print("Cantidad inválida.")
        elif cantidad_compra > gorras[codigo]['cantidad']:
            print("No hay suficientes unidades disponibles.")
        else:
            gorras[codigo]['cantidad'] -= cantidad_compra
            total = cantidad_compra * gorras[codigo]['precio']
            print(f"Compra realizada con éxito. Total a pagar: ${total:.2f}")
    except ValueError:
        print("Por favor ingrese una cantidad válida.")
