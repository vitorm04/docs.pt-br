---
title: Ativação de UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: c0b351adb0b45f42404e94c74bdcff7785c2d0ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143714"
---
# <a name="udp-activation"></a>Ativação de UDP
Esta amostra é baseada na amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md) Ele estende a amostra [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) para suportar a ativação do processo usando o Serviço de Ativação de Processos do Windows (WAS).  
  
 A amostra consiste em três peças principais:  
  
- Um Ativador de Protocolo UDP, um processo autônomo que recebe mensagens UDP em nome de aplicativos que devem ser ativados.  
  
- Um cliente que usa o transporte personalizado UDP para enviar mensagens.  
  
- Um serviço (hospedado em um processo de trabalhador ativado pela WAS) que recebe mensagens sobre o transporte personalizado UDP.  
  
## <a name="udp-protocol-activator"></a>Ativador de protocolo UDP  
 O Ativador de Protocolo UDP é uma ponte entre o cliente WCF e o serviço WCF. Fornece comunicação de dados através do protocolo UDP na camada de transporte. Tem duas funções principais:  
  
- WAS Listener Adapter (LA), que colabora com a WAS para ativar processos em resposta às mensagens recebidas.  
  
- UDP Protocol Listener, que aceita mensagens UDP em nome de aplicativos que devem ser ativados.  
  
 O ativador deve estar sendo executado como um programa autônomo na máquina do servidor. Normalmente, os adaptadores de ouvinte WAS (como o NetTcpActivator e o NetPipeActivator) são implementados em serviços windows de longa duração. No entanto, para simplicidade e clareza, esta amostra implementa o ativador de protocolo como um aplicativo autônomo.  
  
### <a name="was-listener-adapter"></a>WAS Adaptador de ouvinte  
 O adaptador de ouvinte WAS para UDP é implementado na `UdpListenerAdapter` classe. É o módulo que interage com o WAS para realizar a ativação do aplicativo para o protocolo UDP. Isso é conseguido chamando as seguintes APIs do Webhost:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Após a `WebhostRegisterProtocol`chamada inicialmente, o adaptador de ouvinte recebe o retorno `ApplicationCreated` de chamada do WAS para todos os aplicativos registrados no aplicativoHost.config (localizado em %windir%\system32\inetsrv). Nesta amostra, apenas lidamos com os aplicativos com o protocolo UDP (com o id de protocolo como "net.udp") ativado. Outras implementações podem lidar com isso de forma diferente se essas implementações responderem a alterações dinâmicas de configuração no aplicativo (por exemplo, uma transição de aplicativo de desativado para habilitado).  
  
 Quando o `ConfigManagerInitializationCompleted` retorno de chamada é recebido, indica que o WAS tenha terminado todas as notificações para a inicialização do protocolo. Neste momento, o adaptador de ouvinte está pronto para processar solicitações de ativação.  
  
 Quando uma nova solicitação chega na primeira vez para um `WebhostOpenListenerChannelInstance` aplicativo, o adaptador de ouvinte liga para o WAS, que inicia o processo do trabalhador se ele ainda não for iniciado. Em seguida, os manipuladores de protocolo são carregados e a comunicação entre o adaptador ouvinte e o aplicativo virtual pode começar.  
  
 O adaptador de ouvinte está registrado na seção %SystemRoot%\System32\inetsrv\ApplicationHost.config na seção <`listenerAdapters`>:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Ouvinte de Protocolo  
 O ouvinte de protocolo UDP é um módulo dentro do ativador de protocolo que ouve em um ponto final UDP em nome do aplicativo virtual. É implementado na `UdpSocketListener`classe. O ponto final `IPEndpoint` é representado como para o qual o número da porta é extraído da vinculação do protocolo para o site.  
  
### <a name="control-service"></a>Serviço de Controle  
 Nesta amostra, utilizamos o WCF para comunicar entre o ativador e o processo do trabalhador WAS. O serviço que reside no ativador é chamado de Serviço de Controle.  
  
## <a name="protocol-handlers"></a>Manipuladores de protocolo  
 Após as chamadas `WebhostOpenListenerChannelInstance`do adaptador de ouvinte, o gerente de processo WAS inicia o processo do trabalhador se ele não for iniciado. O gerenciador de aplicativos dentro do processo do trabalhador então carrega o PPH (Process Protocol Handler, manipulador de protocolo de processo udp) com a solicitação para isso `ListenerChannelId`. O PPH em `IAdphManager`turnos chamadas .`StartAppDomainProtocolListenerChannel` para iniciar o UDP AppDomain Protocol Handler (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>Configuração hostedUDPTransporte  
 As informações estão registradas no Web.config da seguinte forma:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Configuração especial para esta amostra  
 Esta amostra só pode ser construída e executada no Windows Vista, Windows Server 2008 ou Windows 7. Para executar a amostra, primeiro você deve obter todos os componentes configurados corretamente. Use as seguintes etapas para instalar a amostra.  
  
#### <a name="to-set-up-this-sample"></a>Para configurar este exemplo  
  
1. Instale ASP.NET 4.0 usando o seguinte comando.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Construa o projeto no Windows Vista. Após a compilação, ele também executa as seguintes operações na fase pós-compilação:  
  
    - Instala a vinculação udp ao site "Site padrão".  
  
    - Cria o aplicativo virtual "ServiceModelSamples" para apontar para o caminho físico: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Ele também permite o protocolo "net.udp" para este aplicativo virtual.  
  
3. Inicie o aplicativo de interface de usuário "WasNetActivator.exe". Clique na guia **Configuração,** verifique as seguintes caixas de seleção e clique **em Instalar** para instalá-las:  
  
    - Adaptador de ouvinte UDP  
  
    - Manipuladores de protocolo UDP  
  
4. Clique na guia **Ativação** do aplicativo de interface do usuário "WasNetActivator.exe". Clique no botão **Iniciar** para iniciar o adaptador de ouvinte. Agora você está pronto para executar o programa.  
  
    > [!NOTE]
    > Quando você terminar com esta amostra, você deve executar Cleanup.bat para remover a vinculação net.udp do "Site da Web padrão".  
  
## <a name="sample-usage"></a>Exemplo de uso  
 Após a compilação, há quatro binários diferentes gerados:  
  
- Cliente.exe: O código do cliente. A configuração App.config é compilada no arquivo de configuração cliente Client.exe.config.  
  
- UDPActivation.dll: a biblioteca que contém todas as principais implementações de UDP.  
  
- Service.dll: O código de serviço. Isso é copiado para o diretório \bin do aplicativo virtual ServiceModelSamples. O arquivo de serviço é Service.svc e o arquivo de configuração é Web.config. Após a compilação, eles são copiados para o seguinte local: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: O programa ativador UDP.  
  
- Certifique-se de que todas as peças necessárias estejam instaladas corretamente. As etapas a seguir mostram como executar a amostra:  
  
1. Certifique-se de que os seguintes serviços do Windows foram iniciados:  
  
    - Serviço de ativação de processos do Windows (WAS).  
  
    - Serviços de Informação na Internet (IIS): W3SVC.  
  
2. Em seguida, inicie o ativador, WasNetActivator.exe. Na guia **Ativação,** o único protocolo, **UDP,** é selecionado na lista de desímparadas. Clique no botão **Iniciar** para iniciar o ativador.  
  
3. Uma vez iniciado o ativador, você pode executar o código do cliente executando Client.exe a partir de uma janela de comando. A seguir está a saída da amostra:  
  
    ```console  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
