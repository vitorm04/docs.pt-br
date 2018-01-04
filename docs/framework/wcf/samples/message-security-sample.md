---
title: "Exemplo de segurança de mensagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
caps.latest.revision: "33"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a26356346ca3dfea858f286dd32cb08b0e3b3591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-sample"></a>Exemplo de segurança de mensagem
Este exemplo demonstra como implementar um aplicativo que usa o `basicHttpBinding` e segurança de mensagem. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O modo de segurança de `basicHttpBinding` podem ser definidas para os seguintes valores: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` e `None`. No seguinte exemplo serviço App. config arquivo, a definição de ponto de extremidade Especifica o `basicHttpBinding` e faz referência a uma configuração de associação denominada `Binding1`, conforme mostrado no exemplo de configuração:  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>   …  
</system.serviceModel>  
```  
  
 Os conjuntos de configuração de associação de `mode` atributo do [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) para `Message` e define o `clientCredentialType` atributo do [ \<mensagem >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)para `Certificate` conforme mostrado no exemplo de configuração:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 O certificado que o serviço usa para se autenticar para o cliente é definido na seção do arquivo de configuração em comportamentos a `serviceCredentials` elemento. O modo de validação que se aplica ao certificado que o cliente usa para se autenticar para o serviço também é definido na seção comportamentos no `clientCertificate` elemento.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 O mesmo detalhes de associação e segurança é especificado no arquivo de configuração do cliente.  
  
 A identidade do chamador é exibida na janela do console de serviço usando o código a seguir:  
  
```  
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Para configurar e criar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo no mesmo computador  
  
1.  Execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo.  
  
    > [!NOTE]
    >  O arquivo em lotes bat é projetado para ser executado de um Prompt de comando do SDK do Windows. Isso requer que a variável de ambiente MSSDK apontar para o diretório onde o SDK está instalado. Essa variável de ambiente é definida automaticamente em um Prompt de comando do SDK do Windows.  
  
2.  Execute o aplicativo de serviço do \service\bin.  
  
3.  Execute o aplicativo cliente de \Client\Bin. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Remova os certificados executando Cleanup.bat quando você tiver terminado com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo em computadores  
  
1.  Crie um diretório no computador de serviço para os binários de serviço.  
  
2.  Copie os arquivos de programa do serviço para o diretório de serviço no servidor. Também copie os arquivos. bat, Cleanup.bat e ImportClientCert.bat para o servidor.  
  
3.  Crie um diretório no computador cliente para os binários do cliente.  
  
4.  Copie os arquivos de programa do cliente para o diretório de cliente no computador cliente. Também copie os arquivos. bat, Cleanup.bat e ImportServiceCert.bat ao cliente.  
  
5.  No servidor, execute `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
6.  Editar Service.exe.config para refletir o novo nome de certificado (no `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) elemento) que é o mesmo que o nome de domínio totalmente qualificado da máquina. Também alterar o valor do endereço base para especificar um nome de computador totalmente qualificado em vez de localhost`.`  
  
7.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
8.  No cliente, execute `setup.bat client`. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado client.com e exporta o certificado de cliente para um arquivo chamado cer.  
  
9. No arquivo Client.exe.config no computador cliente, altere o valor do endereço do ponto de extremidade para coincidir com o novo endereço do seu serviço. Para fazer isso, substituindo o host local com o nome de domínio totalmente qualificado do servidor. Alterar também o `findValue` atributo do [ \<defaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) para o novo nome de certificado de serviço que é o nome de domínio totalmente qualificado do servidor.  
  
10. Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.  
  
11. No cliente, execute ImportServiceCert.bat. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.  
  
12. No servidor, execute ImportClientCert.bat, isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
13. No computador de serviço, execute Service.exe em um prompt de comando.  
  
14. No computador cliente, inicie Client.exe em uma janela de prompt de comando.  
  
    1.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre máquinas. Se você tiver executado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos que usam certificados em computadores, certifique-se de desmarcar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` por exemplo:`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
  
## <a name="see-also"></a>Consulte também
