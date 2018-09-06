---
title: Ativação TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c10cc1edfb06d55fc8a59a32bf905c95b20a19dc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799353"
---
# <a name="tcp-activation"></a>Ativação TCP
Este exemplo demonstra como hospedar um serviço que usa Windows processo WAS (Activation Services) para ativar um serviço que se comunica através do protocolo NET. TCP. Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 O exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedado em um processo de trabalho ativado pelo WAS. Atividade do cliente está visível na janela do console.  
  
 O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir), conforme mostrado no código de exemplo a seguir:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 A implementação do serviço calcula e retorna o resultado apropriado:  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 O exemplo usa uma variante do NET. TCP associação com segurança desativada e o compartilhamento de porta do TCP está habilitado. Se você quiser usar uma associação segura de TCP, altere o modo de segurança do servidor para a configuração desejada e execute novamente o Svcutil.exe no cliente para gerar um arquivo de configuração de cliente de atualização.  
  
 O exemplo a seguir mostra a configuração para o serviço:  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="PortSharingBinding" portSharingEnabled="true">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 Ponto de extremidade do cliente é configurado como mostrado no código de exemplo a seguir:  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <netTcpBinding>  
          <binding name="NetTcpBinding_ICalculator">  
            <security mode="None"/>  
          </binding>  
        </netTcpBinding>  
    </bindings>  
    <client>  
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"  
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />  
    </client>  
</system.serviceModel>  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que [!INCLUDE[iisver](../../../../includes/iisver-md.md)] está instalado. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] é necessário para a ativação do WAS.  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Além disso, você deve instalar os componentes de ativação não HTTP do WCF:  
  
    1.  Dos **inicie** menu, escolha **painel de controle**.  
  
    2.  Selecione **programas e recursos**.  
  
    3.  Clique em **ativar ou desativar a componentes do Windows**.  
  
    4.  Expanda o **Microsoft .NET Framework 3.0** nó e verifique se o **ativação não HTTP do Windows Communication Foundation** recurso.  
  
3.  Configure o WAS para dar suporte à ativação de TCP.  
  
     Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado AddNetTcpSiteBinding.cmd localizado no diretório de exemplo.  
  
    1.  Para dar suporte à ativação de NET. TCP, o site padrão primeiro deve ser associado a uma porta NET. TCP. Isso pode ser feito usando Appcmd.exe, que é instalado com o conjunto de ferramentas de gerenciamento do Internet Information Services 7.0 (IIS). Em um prompt de comando com nível de administrador, execute o seguinte comando:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  Esse comando é uma única linha de texto. Este comando adiciona uma associação de site do NET. TCP para o site padrão escuta na porta TCP 808 com qualquer nome de host.  
  
    2.  Embora todos os aplicativos dentro de um site compartilham uma associação comum de NET. TCP, cada aplicativo pode habilitar o suporte do NET. TCP individualmente. Para habilitar o NET. TCP para o aplicativo /servicemodelsamples, execute o seguinte comando em um prompt de comando com nível de administrador:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto. Este comando habilita o aplicativo /servicemodelsamples sejam acessados usando ambos http://localhost/servicemodelsamples e net.tcp://localhost/servicemodelsamples.  
  
4.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
     Remova a associação de site do NET. TCP que é adicionado para este exemplo.  
  
     Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding.cmd localizado no diretório de exemplo.  
  
    1.  Remova NET. TCP da lista de protocolos habilitados, executando o seguinte comando em um prompt de comando com nível de administrador:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Esse comando deve ser inserido como uma única linha de texto.  
  
    2.  Remova a associação do site NET. TCP, executando o seguinte comando em um prompt de comando com nível de administrador:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Esse comando deve ser digitado como uma única linha de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
