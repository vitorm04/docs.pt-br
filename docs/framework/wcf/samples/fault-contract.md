---
title: Contrato de falha
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 39bb9b0ebd9feb6066c1c5e83128eb3a594d6d99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653925"
---
# <a name="fault-contract"></a>Contrato de falha
O exemplo de contrato de falha demonstra como se comunicar informações de erro de um serviço para um cliente. O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna para uma falha. O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O contrato de Calculadora foi modificado para incluir um <xref:System.ServiceModel.FaultContractAttribute> conforme mostrado no código de exemplo a seguir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo indica que o `Divide` operação poderá retornar uma falha do tipo `MathFault`. Uma falha pode ser de qualquer tipo que pode ser serializado. Nesse caso, o `MathFault` é um contrato de dados, da seguinte maneira:  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 O `Divide` método lança um <xref:System.ServiceModel.FaultException%601> ocorrerá uma exceção quando uma divisão por zero exceção conforme mostrado no código de exemplo a seguir. Essa exceção resulta em uma falha que está sendo enviada ao cliente.  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 O código do cliente força um erro ao solicitar uma divisão por zero. Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Você pode ver a divisão por zero, que está sendo relatado como uma falha. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 O cliente faz isso capturando apropriado `FaultException<MathFault>` exceção:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Por padrão, os detalhes de exceções inesperadas não são enviados ao cliente para impedir que os detalhes da implementação do serviço de escape de limite seguro do serviço. `FaultContract` Fornece uma maneira de descrever as falhas em um contrato e marcar a determinados tipos de exceções, conforme apropriado para a transmissão para o cliente. `FaultException<T>` fornece o mecanismo de tempo de execução para o envio de falhas para consumidores.  
  
 No entanto, é útil ver os detalhes internos de uma falha de serviço durante a depuração. Para desativar o comportamento seguro descrito anteriormente, você pode indicar que os detalhes de cada exceção sem tratamento no servidor devem ser incluídos na falha que é enviada ao cliente. Isso é feito definindo <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> para `true`. Você pode defini-lo no código ou na configuração, conforme mostrado no exemplo a seguir.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Além disso, o comportamento deve ser associado ao serviço, definindo o `behaviorConfiguration` atributo do serviço no arquivo de configuração para "CalculatorServiceBehavior".  
  
 Para capturar essas falhas no cliente, a não-genérica <xref:System.ServiceModel.FaultException> deve ser capturada.  
  
 Esse comportamento só deve ser usado para fins de depuração e nunca deve ser habilitado em produção.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Consulte também
