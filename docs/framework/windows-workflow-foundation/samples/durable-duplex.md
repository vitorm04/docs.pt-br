---
title: "Frente e verso durável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 014604262952d3aef3676318042ae3c96dc07c89
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="durable-duplex"></a>Frente e verso durável
Este exemplo demonstra como configurar e configurar a troca de dois lados durável de mensagem usando as atividades de mensagem em [!INCLUDE[wf](../../../../includes/wf-md.md)]. Uma troca frente e verso durável de mensagem é uma troca bidirecional de mensagem que ocorra um longo período de tempo. O tempo de vida de troca de mensagem pode ser maior que o tempo de vida do canal de comunicação e o tempo de vida de memória das instâncias de serviço.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Nesse exemplo, dois serviços de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementados usando [!INCLUDE[wf2](../../../../includes/wf2-md.md)] são configurados para ter uma troca frente e verso durável de mensagem. A troca de mensagens duplex durável é composta de duas mensagens unidirecionais enviadas através de MSMQ e correlacionados usando [.NET contexto Exchange](http://go.microsoft.com/fwlink/?LinkID=166059). As mensagens são enviadas usando as atividades de mensagem de <xref:System.ServiceModel.Activities.Send> e de <xref:System.ServiceModel.Activities.Receive> . O contexto - .NET é usado especificar o endereço de retorno de chamada nas mensagens enviadas. Ambos os serviços são hospedados usando serviços de ativação de processo do Windows (WAS) e configurados para ativar persistência de instâncias de serviços.  
  
 O primeiro serviço (Service1.xamlx) envia uma solicitação para o serviço de enviar (Service2.xamlx) fazer qualquer trabalho. O trabalho é concluído uma vez, envia de Service2.xamlx uma notificação de volta a Service1.xamlx para indicar que o trabalho foi concluído. Um aplicativo de console do fluxo de trabalho configura as filas que os serviços são escuta sobre e envia a mensagem inicial de Início para ativar Service1.xamlx. Uma vez que Service1.xamlx recebe notificação de Service2.xamlx que o aplicativo trabalho foi concluído, Service1.xamlx salva o resultado a um arquivo XML. Enquanto aguarda a mensagem de retorno de chamada, Service1.xamlx mantém o estado da instância que usa <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>padrão. Service2.xamlx mantém o estado da instância como parte de concluir o trabalho solicitado por Service1.xamlx.  
  
 Para configurar os serviços para usar o contexto - .NET sobre MSMQ, ambos os serviços são configurados para usar uma associação personalizado que consiste em <xref:System.ServiceModel.Channels.ContextBindingElement> e em <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Um endereço de retorno de chamada é especificado com <xref:System.ServiceModel.Channels.ContextBindingElement> e incluído em um cabeçalho de contexto de retorno de chamada com todas as mensagens enviadas usando uma associação personalizado. O exemplo a seguir define a associação personalizado.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  A associação usada por este exemplo não é seguro. Para implantar seu aplicativo você deve configurar a associação com base nos requisitos de segurança do seu aplicativo.  
  
> [!NOTE]
>  Filas usadas neste exemplo não são transacionais. Para obter um exemplo que mostra como configurar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usando filas de transação de trocas de mensagens, consulte o [ativação MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) exemplo.  
  
 A mensagem enviada por Service1.xamlx a Service2.xamlx é enviada usando um ponto final do cliente configurado com o endereço de Service2.xamlx e associação personalizado definido anteriormente. O retorno de chamada de Service2.xamlx a Service1.xamlx é enviado usando um ponto final do cliente sem o endereço explicitamente configurado como o endereço é tirado de contexto de retorno de chamada enviado por Service1.xamlx. O exemplo de código a seguir define os pontos de extremidade de cliente.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 O exemplo de código expõe pontos de extremidade usando essa associação personalizado modificar o mapeamento padrão de protocolo para que os endereços de base de net.msmq usar essa associação personalizado.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 O exemplo de código permite a persistência para ambos os serviços adicionando o comportamento de <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> a ambos os serviços e especificando a cadeia de conexão para o base de dados de persistência.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a>Requisitos de sistema  
 Este exemplo requer os seguintes componentes.  
  
1.  Serviços de Informações da Internet.  
  
2.  Serviços de Informações da Internet -> de gerenciamento do IIS 6.0 -> compatibilidade IIS Metabase e a compatibilidade de configuração do IIS 6.0.  
  
3.  O World Wide Web serviços -> recursos de desenvolvimento de aplicativos -> ao ASP.NET.  
  
4.  Servidor das filas de mensagens da Microsoft (MSMQ).  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Configurar o base de dados de persistência e o diretório de resultados.  
  
    1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Navegue até a pasta para esse exemplo e Setup.cmd executado.  
  
2.  Configurar o aplicativo virtual.  
  
    1.  De um prompt de comando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] , registrar o ASP.NET executando o comando a seguir.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Executar [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões de administrador clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e selecionando **executar como administrador**.  
  
    3.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de DurableDuplex.sln.  
  
3.  Configurar as filas do serviço.  
  
    1.  Para executar o cliente de DurableDuplex, pressione F5.  
  
    2.  Abra o **gerenciamento do computador** console executando `Compmgmt.msc` em um prompt de comando.  
  
    3.  Expanda **serviços e aplicativos**, **enfileiramento**. **Filas particulares**.  
  
    4.  As filas de durableduplex/service1.xamlx e durableduplex/service2.xamlx e selecione **propriedades**.  
  
    5.  Selecione o **segurança** guia e permitir **todos receber mensagem**, **inspecionar mensagem** e **enviar mensagem** permissões para ambas as filas.  
  
    6.  Abra o Gerenciador do IIS (Serviços de Informações da Internet).  
  
    7.  Navegue até **servidor**, **Sites**, **site da Web padrão**, **privada**, **Duplex durável** e selecione **Opções avançadas**.  
  
    8.  Alterar o **protocolos habilitados** para **http,net.msmq**.  
  
4.  Executar o exemplo.  
  
    1.  Navegue para http://localhost/private/durableduplex/service1.xamlx e a http://localhost/private/durableduplex/service2.xamlx para garantir que ambos os serviços estão em execução.  
  
    2.  Pressione F5 para executar DurableDuplexClient.  
  
         Quando a troca de dois lados durável de mensagem concluir um arquivo de result.xml é salvo para a pasta de C:\Inbox e contém o resultado de troca de mensagem.  
  
#### <a name="to-cleanup-optional"></a>A limpeza (opcional)  
  
1.  Execução Cleanup.cmd.  
  
    1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Navegue até a pasta para esse exemplo e Cleanup.cmd executado.  
  
2.  Remova o aplicativo virtual para os serviços.  
  
    1.  Abra o Gerenciador de serviços de informações da Internet (IIS) executando `Inetmgr.exe` em um prompt de comando.  
  
    2.  Navegue até o site da Web padrão e remover o **privada** diretório virtual.  
  
3.  Remover a configuração das filas para esse exemplo.  
  
    1.  Abra o console de gerenciamento do computador executando `Compmgmt.msc` em um prompt de comando.  
  
    2.  Expanda **serviços e aplicativos**, **enfileiramento**, **filas particulares**.  
  
    3.  Excluir o durableduplex/service1.xamlx e filas de durableduplex/service2.xamlx.  
  
4.  Remova o diretório de C:\Inbox.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`