---
title: "Como hospedar um serviço WCF em um serviço Windows gerenciado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8572541e0bf9ddcfb93939c177b5cb8c440b41
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a>Como hospedar um serviço WCF em um serviço Windows gerenciado
Este tópico descreve as etapas básicas necessárias para criar um serviço [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que é hospedado por um serviço Windows. O cenário é habilitado pela opção de hospedagem do serviço Windows gerenciado, que é um serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de execução longa, hospedado fora do IIS (Serviços de Informações da Internet), em um ambiente seguro que não é ativado por mensagem. O tempo de vida do serviço é controlado pelo sistema operacional. Essa opção de hospedagem está disponível em todas as versões do Windows.  
  
 Os serviços Windows podem ser gerenciados com o Microsoft.ManagementConsole.SnapIn no MMC (Console de Gerenciamento Microsoft) e podem ser configurados para início automático quando o sistema for inicializado. Essa opção de hospedagem consiste em registrar o domínio do aplicativo (AppDomain) que hospeda um serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] como um serviço Windows gerenciado para que o tempo de vida de processo do serviço seja controlado pelo SCM (Gerenciador de Controle de Serviço) de serviços Windows.  
  
 O código do serviço inclui uma implementação de serviço do contrato do serviço, de uma classe do serviço Windows e de uma classe de instalador. A classe de implementação de serviço, `CalculatorService`, é um serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. O `CalculatorWindowsService` é um serviço Windows. Para qualificar-se como um serviço Windows, a classe herda de `ServiceBase` e implementa os métodos `OnStart` e `OnStop`. Em `OnStart`, um <xref:System.ServiceModel.ServiceHost> é criado para o tipo `CalculatorService` e é aberto. Em `OnStop`, o serviço é interrompido e descartado. O host também é responsável por fornecer um endereço básico ao host de serviço, que foi configurado nas configurações do aplicativo. A classe de instalador, que herda de <xref:System.Configuration.Install.Installer>, permite que o programa seja instalado como um serviço Windows pela ferramenta Installutil.exe.  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a>Construir o serviço e fornecer o código de hospedagem  
  
1.  Crie um novo projeto de Aplicativo de Console do Visual Studio chamado "Serviço".  
  
2.  Renomeie Program.cs como Service.cs.  
  
3.  Altere o namespace para Microsoft.ServiceModel.Samples.  
  
4.  Adicione referências aos assemblies a seguir.  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceProcess.dll  
  
    -   System.Configuration.Install.dll  
  
5.  Adicione as instruções de uso a seguir a Service.cs.  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  Defina o contrato de serviço `ICalculator` como mostrado no código a seguir.  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  Implemente o contrato de serviço em uma classe chamada `CalculatorService` como mostrado no código a seguir.  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  Crie uma nova classe chamada `CalculatorWindowsService` que herda da classe <xref:System.ServiceProcess.ServiceBase>. Adicione uma variável local chamada `serviceHost` para fazer referência à instância <xref:System.ServiceModel.ServiceHost>. Defina o método `Main` que chama `ServiceBase.Run(new CalculatorWindowsService)`  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. Substitua o método <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> criando e abrindo uma nova instância <xref:System.ServiceModel.ServiceHost> como mostrado no código a seguir.  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. Substitua o método <xref:System.ServiceProcess.ServiceBase.OnStop%2A> fechando <xref:System.ServiceModel.ServiceHost> como mostrado no código a seguir.  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. Crie uma nova classe chamada `ProjectInstaller` que herda de <xref:System.Configuration.Install.Installer> e que é marcada com <xref:System.ComponentModel.RunInstallerAttribute> definido como `true`. Isso permite que o serviço Windows seja instalado pela ferramenta Installutil.exe.  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. Remova a classe `Service` que foi gerada quando você criou o projeto.  
  
13. Adicione um arquivo de configuração de aplicativo ao projeto. Substitua o conteúdo do arquivo pelo XML de configuração a seguir.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     O arquivo App. config no clique com botão direito do **Solution Explorer** e selecione **propriedades**. Em **copiar para diretório de saída** selecione **Copy if Newer**.  
  
     Este exemplo especifica explicitamente pontos de extremidade no arquivo de configuração. Se você não adicionar nenhum ponto de extremidade ao serviço, o tempo de execução adicionará pontos de extremidade padrão para você. Neste exemplo, como o serviço tem <xref:System.ServiceModel.Description.ServiceMetadataBehavior> definido como `true`, seu serviço também possui metadados de publicação habilitados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
### <a name="install-and-run-the-service"></a>Instalar e executar o serviço  
  
1.  Crie a solução para criar o executável `Service.exe`.  
  
2.  Abra o prompt de comando do [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e navegue até o diretório do projeto. Tipo `installutil bin\service.exe` no prompt de comando para instalar o serviço do Windows.  
  
    > [!NOTE]
    >  Se você não usar o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt de comando, certifique-se de que o `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` diretório está no caminho do sistema.  
  
     Digite `services.msc` no prompt de comando para acessar o SCM. O serviço Windows deve aparecer em Serviços como “WCFWindowsServiceSample”. O serviço [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] só poderá responder aos clientes se o serviço Windows estiver em execução. Para iniciar o serviço, clique duas vezes no SCM e selecione "Iniciar" ou tipo **net start-WCFWindowsServiceSample** no prompt de comando.  
  
3.  Se você fizer alterações no serviço, interrompa-o primeiro e desinstale-o. Para parar o serviço, o serviço no SCM e selecione "Stop", ou **net pause do tipo WCFWindowsServiceSample** no prompt de comando. Observe que se você interromper o serviço Windows e executar um cliente, uma exceção <xref:System.ServiceModel.EndpointNotFoundException> ocorrerá quando o cliente tentar acessar o serviço. Para desinstalar o tipo de serviço do Windows **installutil/u bin\service.exe** no prompt de comando.  
  
## <a name="example"></a>Exemplo  
 Veja a seguir uma listagem completa do código usado por este tópico.  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 Como a opção de "auto-hospedagem", o ambiente de hospedagem de serviços Windows requer que algum código de hospedagem seja criado como parte do aplicativo. O serviço é implementado como um aplicativo de console e contém seu próprio código de hospedagem. Em outros ambientes de hospedagem, como o WAS (Serviço de Ativação de Processos do Windows), hospedado no IIS, não é necessário que os desenvolvedores criem código de hospedagem.  
  
## <a name="see-also"></a>Consulte também  
 [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) (Configuração simplificada)  
 [Hospedando em um aplicativo gerenciado](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [Hosting Services](../../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
