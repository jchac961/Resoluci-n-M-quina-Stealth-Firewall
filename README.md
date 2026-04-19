# Resoluci-n-M-quina-Stealth-Firewall
Máquina de la página www.whoami-labs.com

Antes que nada inicie la máquina vulnerable

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-13 200523" src="https://github.com/user-attachments/assets/31483590-be33-4aef-9d40-acf1d26e15ee" />

# Reconocimiento

Una vez iniciada la máquina hacemos un escaneo de puertos utilizando la herramienta nmpap, al mismo tiempo solicitamos a la herramienta nos pueda enviar la versión de servicio que se encuentra ejecutando en los puertos que se encuentren abiertos

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-13 201304" src="https://github.com/user-attachments/assets/cff83a53-a074-42fe-8b85-e72d47eec4c0" />

Ya que vimos que los puertos abiertos que encontro la máquina fueron #22, #80, #2222, #3306, #5432, #8080, #8443, fuimos a un buscador a ver que podiamos encontrar, no fue mucho!! solo un cuadro de inicio de sesión en el cual nos solicitaba un código y podiamos ingresar comandos

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-18 235331" src="https://github.com/user-attachments/assets/71eea1f9-5d52-4628-827d-6f6c40303b23" />

Hice un fuzzing para ver que mas podia encontrar, pero no fue la gran cosa que habia PD: olvide tomar capturas del fuzzing

Luego me propuse a hacer un ataque de fuerza bruta en busca de vr si la máquina podia enconrar el codigo para el inicio de sesión, y en efecto la máquina encontro el codigo asi que me propuse a utilizarlo a ver si era funcional 

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-15 235753" src="https://github.com/user-attachments/assets/b08a4209-2cef-4f97-9808-0a7f4029ea02" />

# Explotación

Utilice el codigo encontrado, con un comando de bash el cual me permitia obtener una reverse shell a mi máquina

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-16 000850" src="https://github.com/user-attachments/assets/578c9513-32b2-4036-bede-09bb8802f2bc" />

Ya tenia una máquina en modo escucha esperando obtener la reverse shell

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-16 000857" src="https://github.com/user-attachments/assets/7187a63e-3d1a-424c-bb6e-cc546e43b690" />

Ya dentro de la máquina liste los binarios en busca de alguno que tuviera mala configuración, y encontramos 3 que nos llamo mucho la atención asi que procedi a utilizarlos

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-16 000944" src="https://github.com/user-attachments/assets/ed6f9a26-bc6d-42bd-9ae7-04a923672b6a" />

Intente utilizar algunos comandos en busca de poder obtener acceso como root pero no pude, asi que procedi a utilizar el binario CAT a ver si me mostraba la flag, y en efecto obtuve su contenido

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-16 002027" src="https://github.com/user-attachments/assets/39187dc0-a6ee-4525-86f2-8bbd59b1ed4d" />

# Escalada de Privilegios

No estaba conforme ya que queria poder escalar privilegios asi que investigue un poco y supe que podia agregr un usario con privilegios de root asi qu procedi a hacer el proceso

Cree el usuario y conttraseña, el cual esta subrayado ya que habia hecho otros intentos pero no habia podido obtener la sesión como root, talvez por algna mala configuración, hasta que al final siempre lo logre con el usuario joseph

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-18 234452" src="https://github.com/user-attachments/assets/14280dbc-6238-4226-b049-ada9b38a3649" />

# Resultados

Una vez dentro busque la flag

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-18 234418" src="https://github.com/user-attachments/assets/2d953124-88d2-4512-a4f0-509a1f947d3b" />

Máquina Powned

<img width="1920" height="1140" alt="Captura de pantalla 2026-04-19 001147" src="https://github.com/user-attachments/assets/fd236fa2-c6e9-4738-a216-83dd78bcf6a9" />




