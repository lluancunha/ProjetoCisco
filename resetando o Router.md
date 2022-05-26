                                                                        resetando o Router

OBSERVAÇÃO: Utilizar o PuTTY para acessar o Switch via Cabo Console.

#01_ Ligar o Router Cisco 2911

#02_ Parar a inicialização do IOS utilizando Ctrl + Break (No PuTTY utilizar Botão direito do 
Mouse na Barra de Título e escolher a opção: Send Command: Break) quando iniciar a descompactação
da Imagem do IOS (mensagem de vários ###########)

CUIDADO!!!!!! com a chave de registro que você vai digitar no ROMmon (veja o tópico Obs1 e 2:)

#03_ Nas configurações do Cisco ROMmon digite a chave em hexadecimal: confreg 0x2142 <Enter>

#04_ Após a mudança, digite: reset <Enter> para reiniciar o Router 2911

#05_ O Router vai inicializar sem ler o arquivo de configuração: startup-config da NVRAM.

#06_ Limpando as configurações do Router 2911 e voltando a ler o arquivo startup-config da NVRAM.
    _06.1. Acessar o modo privilegiado: enable <Enter>
    _06.2. Limpar o arquivo startup-config da NVRAM: erase startup-config <Enter>
    _06.3. Acessar o modo de Configuração Global: configure terminal <Enter>
    _06.4. Mudar o registro de inicialização: config-register 0x2102 <Enter>
    _06.5. Sair de todos os modos: end <Enter>
    _06.6. Salvar o arquivo: running-config para a NVRAM: copy running-config startup-config <Enter>
    _06.7. Reinicializar o router: reload <Enter>
    _06.8. Verificar a chave de registro: enable <Enter>, show version <Enter>

Obs1: caso você digite chaves diferentes na ROMmon o sistema pode inicializar com caracteres estranhos, 
essa falha está associada muitas vezes a velocidade da porta (Padrão 9600), fazer o teste mudando as 
velocidades para: 1200, 2400, 4800, 9600, 19200, 38400, 57600, 115200. 

Obs2: será necessário alterar novamente a chave de registro para: config-register 0x2102 <Enter>
configurar a velocidade do console: line console 0 <Enter>, speed 9600 <Enter>, salvar as
configurações: copy running-config startup-config e reinicializar o router: reload <Enter>
