---
title: NamedPipe Activation
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a4d6612f8d598be6f02def2526920251e36047f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="namedpipe-activation"></a>NamedPipe Activation
Este exemplo demonstra como hospedar um serviço que usa o serviço de ativação de processos do Windows (WAS) para ativar um serviço que se comunica por pipes de nomes. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) e requer [!INCLUDE[wv](../../../../includes/wv-md.md)] para executar.  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O exemplo consiste em um programa de console de cliente (.exe) e uma biblioteca de serviço (. dll) hospedada em um processo de trabalho ativado por serviços de ativação de processos do Windows (WAS). Atividade do cliente estiver visível na janela do console.  
  
 O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir), conforme mostrado no código de exemplo a seguir.  
  
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
  
 O cliente faz solicitações síncronas para uma operação matemática fornecido e a implementação do serviço calcula e retorna o resultado apropriado.  
  
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
  
 O exemplo usa uma modificação `netNamedPipeBinding` associação sem segurança. A associação é especificada nos arquivos de configuração do cliente e do serviço. O tipo de associação para o serviço é especificado no elemento de ponto de extremidade `binding` conforme mostrado no exemplo de configuração do atributo.  
  
 Se você quiser usar uma associação segura de pipe nomeado, altere o modo de segurança do servidor para a configuração de segurança desejado e execute svcutil.exe novamente no cliente para obter o arquivo de configuração de um cliente atualizado.  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
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
  
 Informações de ponto de extremidade do cliente são configuradas como mostrado no código de exemplo a seguir.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que [!INCLUDE[iisver](../../../../includes/iisver-md.md)] está instalado. [!INCLUDE[iisver](../../../../includes/iisver-md.md)] é necessário para a ativação do WAS.  
  
2.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
     Além disso, você deve instalar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes de ativação não HTTP:  
  
    1.  Do **iniciar** menu, escolha **painel de controle**.  
  
    2.  Selecione **programas e recursos**.  
  
    3.  Clique em **ativar ou desativar a componentes do Windows**.  
  
    4.  Expanda o **Microsoft .NET Framework 3.0** nó e verifique se o **ativação não HTTP do Windows Communication Foundation** recurso.  
  
3.  Configure o Windows processo Activation Service (WAS) para dar suporte à ativação de pipe nomeado.  
  
     Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado AddNetPipeSiteBinding.cmd localizado no diretório de exemplo.  
  
    1.  Para dar suporte à ativação do NET. pipe, o site padrão primeiro deve ser associado ao protocolo NET. pipe. Isso pode ser feito usando o appcmd.exe, que é instalado com o conjunto de ferramentas de gerenciamento do IIS 7.0. Em um prompt de comando com privilégios elevados (administrador), execute o seguinte comando.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
         Este comando adiciona uma associação de site do NET. pipe para o site da Web padrão.  
  
    2.  Embora todos os aplicativos dentro de um site compartilham uma associação de pipe comuns, cada aplicativo pode habilitar o suporte de pipe individualmente. Para habilitar o pipe para o aplicativo /servicemodelsamples, execute o seguinte comando em um prompt de comando com privilégios elevados.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
         Este comando permite que o aplicativo /servicemodelsamples ser acessados usando http://localhost/servicemodelsamples e net.tcp://localhost/servicemodelsamples.  
  
4.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Remova a associação de site do NET. pipe adicionado para este exemplo.  
  
     Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetPipeSiteBinding.cmd localizado no diretório de exemplo:  
  
    1.  Remova NET. TCP da lista de protocolos habilitados, executando o seguinte comando em um prompt de comando com privilégios elevados.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Este comando deve ser inserido como uma única linha de texto.  
  
    2.  Remova a associação de site do NET. TCP, executando o seguinte comando em um prompt de comando com privilégios elevados.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  Este comando deve ser digitado em uma única linha de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
