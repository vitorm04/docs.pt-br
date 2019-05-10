---
title: Ativação de UDP
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 158aa804a796f30e7450bda2fadc256ca3579579
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623730"
---
# <a name="udp-activation"></a>Ativação de UDP
Este exemplo se baseia o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo. Ele estende o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo para dar suporte à ativação de processo usando o serviço de ativação de processos do Windows (WAS).  
  
 O exemplo consiste em três partes principais:  
  
- Um ativador de protocolo UDP, um processo autônomo que recebe mensagens UDP em nome dos aplicativos que estão para ser ativado.  
  
- Um cliente que usa o transporte UDP personalizado para enviar mensagens.  
  
- Um serviço (hospedado em um processo de trabalho ativado pelo WAS) que recebe mensagens por meio do transporte UDP personalizado.  
  
## <a name="udp-protocol-activator"></a>Ativador de protocolo UDP  
 O ativador de protocolo UDP é uma ponte entre o cliente do WCF e o serviço do WCF. Ele fornece a comunicação de dados por meio do protocolo UDP na camada de transporte. Ele tem duas funções principais:  
  
- ERA o ouvinte do adaptador (LA), que colabora com WAS para ativar os processos em resposta às mensagens de entrada.  
  
- Ouvinte de protocolo UDP, que aceita mensagens UDP em nome dos aplicativos que estão para ser ativado.  
  
 O ativador deve ser executado como um programa autônomo na máquina do servidor. Normalmente, os adaptadores de escuta do WAS (como o NetTcpActivator e o NetPipeActivator) são implementados nos serviços do Windows de longa execução. No entanto, para manter a simplicidade e clareza, este exemplo implementa o ativador de protocolo como um aplicativo autônomo.  
  
### <a name="was-listener-adapter"></a>FOI o adaptador de escuta  
 O adaptador de escuta foi para UDP é implementado de `UdpListenerAdapter` classe. É o módulo que interage com o WAS para realizar a ativação de aplicativo para o protocolo UDP. Isso é obtido chamando as APIs do Webhost seguintes:  
  
- `WebhostRegisterProtocol`  
  
- `WebhostUnregisterProtocol`  
  
- `WebhostOpenListenerChannelInstance`  
  
- `WebhostCloseAllListenerChannelInstances`  
  
 Depois de chamar inicialmente `WebhostRegisterProtocol`, o adaptador de escuta recebe o retorno de chamada `ApplicationCreated` do WAS para todos os aplicativos registrados no applicationHost. config (localizado em % windir%\system32\inetsrv). Neste exemplo, estamos apenas lidar com os aplicativos com o protocolo UDP (com a id de protocolo como "net.udp") habilitados. Outras implementações podem manipular essa forma diferente se essas implementações respondem a alterações de configuração dinâmica para o aplicativo (por exemplo, uma transição de aplicativos de desabilitado para habilitado).  
  
 Quando o retorno de chamada `ConfigManagerInitializationCompleted` for recebido, ele indica que o WAS concluiu todas as notificações para a inicialização do protocolo. Neste momento, o adaptador de escuta está pronto para processar as solicitações de ativação.  
  
 Quando uma nova solicitação chega na primeira vez para um aplicativo, o adaptador de escuta chama `WebhostOpenListenerChannelInstance` no WAS, que inicia o processo de trabalho se ele ainda não foi iniciado. Em seguida, os manipuladores de protocolo são carregados e a comunicação entre o adaptador de escuta e o aplicativo virtual pode iniciar.  
  
 O adaptador de escuta é registrado no %SYSTEMROOT%\system32\inetsrv\ApplicationHost.config. no <`listenerAdapters`> seção da seguinte maneira:  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a>Ouvinte de protocolo  
 O ouvinte de protocolo UDP é um módulo dentro o ativador de protocolo que escuta em um ponto de extremidade UDP em nome do aplicativo virtual. Ele é implementado na classe `UdpSocketListener`. O ponto de extremidade é representado como `IPEndpoint` para que o número da porta é extraído da associação do protocolo para o site.  
  
### <a name="control-service"></a>Serviço de controle  
 Neste exemplo, usamos o WCF para comunicação entre o ativador e o processo de trabalho do WAS. O serviço que reside o ativador é chamado o serviço de controle.  
  
## <a name="protocol-handlers"></a>Manipuladores de protocolo  
 Depois das chamadas de adaptador do ouvinte `WebhostOpenListenerChannelInstance`, o Gerenciador de processo WAS inicia o processo de trabalho se ele não for iniciado. O Gerenciador de aplicativos dentro do processo de trabalho, em seguida, carrega o UDP processo protocolo manipulador PPH () com a solicitação para que `ListenerChannelId`. O PPH em chamadas desativa `IAdphManager`.`StartAppDomainProtocolListenerChannel` para iniciar o manipulador de protocolo de AppDomain do UDP (ADPH).  
  
## <a name="hostedudptransportconfiguration"></a>HostedUDPTransportConfiguration  
 As informações são registradas no Web. config da seguinte maneira:  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a>Instalação especial para este exemplo  
 Este exemplo pode ser compilado e executado no Windows Vista, Windows Server 2008 ou Windows 7 somente. Para executar o exemplo, você deve primeiro obter todos os componentes configurados corretamente. Use as etapas a seguir para instalar o exemplo.  
  
#### <a name="to-set-up-this-sample"></a>Para configurar este exemplo  
  
1. Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Compile o projeto no Windows Vista. Após a compilação, ele também executa as seguintes operações na fase de pós-compilação:  
  
    - Instala a associação de UDP para o site "Site padrão".  
  
    - Cria o aplicativo virtual "ServiceModelSamples" para apontar para o caminho físico: "% SystemDrive%\inetpub\wwwroot\servicemodelsamples".  
  
    - Ele também habilita o protocolo de "net.udp" para esse aplicativo virtual.  
  
3. Inicie o aplicativo de interface do usuário "WasNetActivator.exe". Clique o **instalação** guia, marque as caixas de seleção a seguir e, em seguida, clique em **instalar** instalá-los:  
  
    - Adaptador de escuta UDP  
  
    - Manipuladores de protocolo UDP  
  
4. Clique o **ativação** guia do aplicativo de interface do usuário "WasNetActivator.exe". Clique o **iniciar** botão para iniciar o adaptador de escuta. Agora você está pronto para executar o programa.  
  
    > [!NOTE]
    >  Quando tiver terminado com este exemplo, você deve executar CleanUp para remover a associação de net.udp de "Site da Web padrão".  
  
## <a name="sample-usage"></a>Uso de exemplo  
 Após a compilação, há quatro binários diferentes gerados:  
  
- Client.exe: O código do cliente. O App. config é compilado para o arquivo de configuração de cliente Client.exe.config.  
  
- UDPActivation.dll: a biblioteca que contém todas as principais implementações de UDP.  
  
- Service.dll: O código de serviço. Isso é copiado para o diretório \bin do aplicativo virtual ServiceModelSamples. O arquivo de serviço é SVC e o arquivo de configuração é Web. config. Após a compilação, eles são copiados no seguinte local: % SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.  
  
- WasNetActivator: O programa de ativador UDP.  
  
- Certifique-se de que todas as partes necessárias estão instaladas corretamente. As etapas a seguir mostram como executar o exemplo:  
  
1. Certifique-se de que os seguintes serviços do Windows foram iniciados:  
  
    - Windows Process Activation Service (WAS).  
  
    - Serviços de informações da Internet (IIS): W3SVC.  
  
2. Em seguida, inicie o ativador, WasNetActivator.exe. Sob o **ativação** guia, o único protocolo, **UDP**, está selecionado na lista suspensa. Clique o **iniciar** botão para iniciar o ativador.  
  
3. Depois que o ativador for iniciado, você pode executar o código do cliente, executando Client.exe em uma janela de comando. Este é o exemplo de saída:  
  
    ```  
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
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
