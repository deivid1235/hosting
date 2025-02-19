from datetime import datetime
import getpass

productos = []
carrito = []

def agregar_productos():
    print("\n-------🏪 Menu de agregar productos a la tiendad  ---------")
    producto = input("Ingrese el nombre del producto: ") .strip()
    talla = int(input("Ingrese la talla del producto: ").strip())
    precio = float(input("Ingrese el precio del producto: ").strip())
    marca = input("Ingrese la marca del producto: ") .strip()
    color = input("Ingrese un color del producto: ")  .strip()
    print("-----------------------------------------------------------")

    accesorios = {
        "producto": producto,
        "talla": talla,
        "precio": precio,
        "marca": marca,
        "color": color
    }
    productos.append(accesorios)
    print("\n ¡Producto agregado corectamente!")

def buscar_productos ():
    print("\n------🏪 Buscar productos en el minimarket -----------")
    producto = input("Ingrese el nombre del producto: ") .strip()
    producto_encontrado = None
    for accesorio in productos:
        if accesorio["producto"].lower() == producto.lower():
            producto_encontrado = accesorio
            break

    if producto_encontrado:
        print("\n---Producto encontrado-------")
        for clave, valor in producto_encontrado.items():
            print(f"{clave.capitalize()}: {valor}")
    else:
        print("\nNo se encontro el producto...")

def lista_productos():
    if not productos:
        print("No hay contactos registrados. ")
    else:
        print("\n---🏪 lista de todos los productos del la minimarket-------- ")
        for i, accesorios in enumerate(productos, start=1):
            print(f"--{i}----")
            print(f"🛒 Producto: {accesorios['producto']}")
            print(f"🛒 Talla : {accesorios['talla']}")
            print(f"💵 Precio:  {accesorios['precio']}")
            print(f"❎ Marca:  {accesorios['marca']}")
            print(f"🌈 Color:  {accesorios['color']}")
            print("---------------------------------------------------------")


def eliminar_producto():
    print("\n🗑️ ----- Eliminar producto del minimarket --------")
    producto_nombre = input("Ingrese el nombre del producto: ").strip()
    
    producto_encontrado = None
    for accesorio in productos:
        if accesorio["producto"].lower() == producto_nombre.lower():
            producto_encontrado = accesorio
            break  

    if producto_encontrado:
        productos.remove(producto_encontrado)  
        print(f"\n✅ Producto '{producto_nombre}' eliminado correctamente.")
    else:
        print("\n❌ No se encontró el producto en la tienda.")


def agregar_carrito():
    print("\n🛒 --- Agregar producto al carrito ---")
    producto_nombre = input("Ingrese el nombre del producto que desea agregar al carrito: ").strip()

    for producto in productos:
        if producto["producto"].lower() == producto_nombre.lower():
            carrito.append(producto)  
            print(f"\n✅ ¡{producto_nombre} agregado al carrito!")
            return  


    print("\n❌ El producto no se encuentra en la tienda.")

def ver_carrito():
    if not carrito:
        print("\n🛒 El carrito está vacío.")
    else:
        print("\n📶 --- Productos en el carrito ---")
        total = 0
        for i, producto in enumerate(carrito, start=1):
            print(f"\n🛒 {i}. Producto: {producto['producto']}")
            print(f"  🛒 Talla: {producto['talla']}")
            print(f"  💵 Precio: S/{producto['precio']}")
            print(f"  ❎ Marca: {producto['marca']}")
            print(f"  🌈 Color: {producto['color']}")
            print("---------------------------------------------------------")
            total += producto['precio']
        print(f"\n💰 Total a pagar: S/{total:.2f}")

        print("\n💳 --- Métodos de pago disponibles ---")
        print("1. Tarjeta de credito/debito")
        print("2. Yape")
        print("3. Efectivo")

        metodo_pago = input("Ingrese un metodo de pago (1-3): ")
        if metodo_pago == "1":
            tarjeta = input("Ingrese el numero de su tarjeta: ").strip()
            cvv = input("Ingrese el CVV de la tarjeta: ").strip()

            print("\n✅------Factura del pago -------")
            print(f"Numero de tarjeta: {tarjeta}")
            print(f"Numero de CVV : {cvv}")
            print("\n✅ Pago exitoso con tarjeta. ¡Gracias por su compra! 🛍️")

        elif metodo_pago == "2":
            print("\n📲 Para pagar con Yape, escanea el código QR o envía el monto a 956092690.")
            print("✅ Pago exitoso con Yape. ¡Gracias por su compra! 🛍️")
        
        elif metodo_pago == "3":
            print("\n💵 Puede pagar en efectivo al recibir el producto.")
            print("✅ Gracias por su compra. 🛍️")
        
        else:
            print("\n❌ Método de pago no válido. Inténtelo nuevamente.")

    

def eliminar_carrito():
    print("\n🗑️ ----- Eliminar producto del carrito --------")
    producto_nombre = input("Ingrese el nombre del producto: ").strip()
    
    producto_encontrado = None
    for accesorio in productos:
        if accesorio["producto"].lower() == producto_nombre.lower():
            producto_encontrado = accesorio
            break  

    if producto_encontrado:
        carrito.remove(producto_encontrado)  
        print(f"\n✅ Producto '{producto_nombre}' eliminado correctamente.")
    else:
        print("\n❌ No se encontró el producto en la tienda.")

def menu():
    while True:
        print("\n--------🏪 Bienvenidos a la tienda iman bruno---------")
        print("1. Agregar productos.  ")
        print("2. Buscar productos. ")
        print("3. Lista de  productos. ")
        print("4. Eliminar productos ")
        print("5. Agregar al carrito. ")
        print("6. Ver porductos en el carrito. ")
        print("7. Eliminar productos en el carrito. ")
        print("8. Salir ")

        opcion = int(input("Ingrese una opcion del (1-7): "))

        if opcion == 1:
            agregar_productos()
        elif opcion == 2:
            buscar_productos()
        elif opcion == 3:
            lista_productos()
        elif opcion == 4:
            eliminar_producto()
        elif opcion == 5:
            agregar_carrito()
        elif opcion == 6:
            ver_carrito()
        elif opcion == 7:
            eliminar_carrito()
        elif opcion == 8:
            print("\n--------🏪Gracias por utilizar el app para realizar sus compras -----")
        else:
            print("\nOpcion incorecto ingrese otro numero ..")


menu()
