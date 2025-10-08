## Installazione della toolchain MinGW-64 (include il compilatore ``gcc``)

1. Scaricare e installare l'ultima versione disponibile del pacchetto **MSYS2** (LINK: [https://github.com/msys2/msys2-installer/releases](https://github.com/msys2/msys2-installer/releases), e cliccare sulla prima voce *Assets*). Selezionare il file di installazione: ci sono due scelte possibili: *msys2-arm64-20250830.exe* (se si possiede processore *ARM*) oppure *msys2-x86_64-20250830.exe* (se si possiede processore *Intel*). Nella fase finale, spuntare l'esecuzione di *MSYS2* (``Run MSYS2 now``). Se non compare la spunta basta avviare la procedura di installazione cliccando due volte sul file scaricato. In genere si trova nella cartella Download.

2. Dopo il doppio clic si aprirà una finestra guidata. Si proceda con l’installazione accettando le opzioni predefinite e cliccando su **Avanti** quando richiesto.

3. Al termine dell'installazione la finestra aperta in precedenza si chiuderà e si aprirà un terminale dove di volta in volta bisogna digitare i seguenti comandi:

	```
	pacman -S --needed base-devel
	pacman -S --needed mingw-w64-ucrt-x86_64-toolchain 
	pacman -S --needed mingw-w64-ucrt-x86_64-clang-tools-extra
	```

	si scelga l'opzione di default per tutti i pacchetti da installare (digitando INVIO), successivamente digitare ``Y``, quando richiesto, e poi INVIO.

4. Al termine dell'istallazione basterà chiudere il terminale come una normale applicazione.

5. Aggiungere la directory ``C:\msys64\ucrt64\bin`` (questo è il percordo di default) al ``PATH`` di sistema di Windows

	* Nella barra di ricerca, aprire le impostazioni e cercare ``Modifica variabili d'ambiente per l'account``

	* Nella sezione ``Variabili dell'utente per ...``, cliccare sulla variabile d'ambiente ``Path``, poi il tasto ``Modifica...``, successivamente il tasto ``Nuovo`` per aggiungere la variabile ``C:\msys64\ucrt64\bin``. Cliccare su ``Ok`` per rendere effettive le modifiche

6. Controllare se l'installazione del compilatore è andata a buon fine, digitando in un nuovo prompt di sistema ``gcc --version``. L'output dovrebbe mostrare, tra le altre informazioni, la versione del compilatore installata.

## Installazione e configurazione VSCodium 

### Installare *VSCodium*

> **_NOTE:_**  *VSCodium* è una distribuzione con licenza libera dell'editor *VSCode* di Microsoft. *VSCode* contiene funzionalità di telemetria e tracciamento, quindi scegliere la versione da installare a propria discrezione. I due IDE sono equivalenti! L'autocompletamento del codice attraverso l'uso delle estensioni disponibili non è attualmente supportato.

E' possibile scaricare l'ultima version dell'installer di *VSCodium* utilizzando il seguente link
[https://github.com/VSCodium/vscodium/releases/](https://github.com/VSCodium/vscodium/releases/), andando a scaricare la versione per *Windows*, tipologia *System Installer*.

### Installare le estensioni C 

Aprire VSCodium e installare l'estensioni **Code Runner** e **clangd** nella vista "Estensioni" (vedere nelle figure seguenti).

![code-runner-extension](code-runner-extension.jpg)

![clangd-extension](clangd-extension.jpg)

Una volta installate l'estensioni, configurare **Code Runner** in modo da utilizzare il terminale di default del proprio sistema operativo. A tale scopo, cliccare sul tasto impostazioni dell'estensione e poi *Impostazioni dell'Estensione (Extension Settings)*:

<p align="center">

<img src="code-runner-extension_terminal_1.jpg" alt="drawing" width="400"/>

</p>

Successivamente digitare "terminal" nella barra di ricerca e spuntare l'opzione "*Code-runner: Run in Terminal*".

<p align="center">

<img src="code-runner-extension_terminal_2.jpg" alt="drawing"/>

</p>

Inoltre, impostare le opzioni *Save All Files Before Run* e *Save File Before Run* come indicato nella seguente figura:

<p align="center">

<img src="code-runner-extension_save.png" alt="drawing"/>

</p>


Una volta installata anche l'estensione *clangd* bisogna specificare il percorso assoluto del **clangd server**, che di default è ``C:\msys64\ucrt64\bin\clangd.exe``. Impostare tale percorso come nelle seguenti figure.

<p align="center">

<img src="clangd-extension_3.png" alt="drawing"/>

</p>

<p align="center">

<img src="clangd-extension_4.png" alt="drawing"/>

</p>


Una volta impostato il Clangd Path riavviare VSCodium.


## Creazione del nostro primo programma (Hello World)

1. Creare una nuova cartella in una posizione qualunque
2. Aprire *VSCodium*, cliccare su ``Open Folder``, selezionare la cartella creata al punto 1.
3. Creare un nuovo file sorgente con estensione ``c`` (e.g., ``main.c``) e scrivere il seguente programma d'esempio:

	```[c]
	#include <stdio.h>
	
	int main(){
	
		printf("HELLO WORLD!!!\n");
		return 0;
	}
	```

4. Cliccare su ``Run`` e scegliere il compilatore ``gcc`` quando richiesto
5. Osservare l'output (la stringa ``HELLO WORLD!!!``) nel tab "Terminale"


