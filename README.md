# daw1b-2425-Entornos-DiagramaEstados1

![image](https://github.com/user-attachments/assets/0a1ca3b3-65f1-4d56-8d52-cd98687dcece)

@startuml
[*] --> StandBy

StandBy --> ValidarTarjeta : Insertar tarjeta
ValidarTarjeta --> StandBy : Tarjeta no válida
ValidarTarjeta --> IntroducirPIN : Tarjeta válida

IntroducirPIN --> IntroducirPIN : PIN incorrecto (intentos < 3)
IntroducirPIN --> RetenerTarjeta : 3 intentos fallidos
IntroducirPIN --> SeleccionTransaccion : PIN correcto
IntroducirPIN --> StandBy : Cancelar

SeleccionTransaccion --> EjecucionTransaccion : Elegir transacción
SeleccionTransaccion --> FinSesion : Cancelar / Finalizar sesión

EjecucionTransaccion --> SeleccionTransaccion : Transacción completada
EjecucionTransaccion --> FinSesion : Finalizar sesión

FinSesion --> ExpulsarTarjeta
ExpulsarTarjeta --> StandBy

RetenerTarjeta --> StandBy
@enduml
