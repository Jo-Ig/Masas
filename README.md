def calculadora_flexible_masa():
    """
    Calcula los ingredientes basado en lo que el usuario conoce
    """
    print("¿Qué valor conoces?")
    print("1. Harina total")
    print("2. Agua total") 
    print("3. Peso final de masa deseado")
    
    opcion = input("Elige una opción (1-3): ")
    
    if opcion == "1":
        harina = float(input("Harina total (g): "))
        hidratacion = float(input("Hidratación (%): ")) / 100
        calcular_desde_harina(harina, hidratacion)
        
    elif opcion == "2":
        agua = float(input("Agua total (g): "))
        hidratacion = float(input("Hidratación (%): ")) / 100
        harina = agua / hidratacion
        calcular_desde_harina(harina, hidratacion)
        
    elif opcion == "3":
        masa_final = float(input("Peso final de masa deseado (g): "))
        # Aproximación considerando fermentación y pérdidas
        harina = masa_final / 1.7
        hidratacion = 0.6  # estándar
        calcular_desde_harina(harina, hidratacion)
        
    else:
        print("Opción no válida")

def calcular_desde_harina(harina_total, hidratacion):
    """Calcula todos los ingredientes desde la harina total"""
    prefermento = calcular_prefermento(harina_total, hidratacion)
    
    print(f"\n=== FÓRMULA PARA {harina_total:.0f}g DE HARINA ===")
    print(f"Hidratación: {hidratacion*100}%")
    print(f"Agua total: {harina_total * hidratacion:.0f}g")
    print(f"Sal: {harina_total * 0.02:.1f}g")
    
    print("\--- Prefermento ---")
    print(f"Harina: {prefermento['harina']:.0f}g")
    print(f"Agua: {prefermento['agua']:.0f}g") 
    print(f"Levadura: {prefermento['levadura']:.2f}g")