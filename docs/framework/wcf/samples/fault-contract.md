---
title: Contrato de falha
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: c8e93f73d150132c9d6750b81ba2ade944808d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183660"
---
# <a name="fault-contract"></a>Contrato de falha
A amostra Contrato de Falha demonstra como comunicar informações de erro de um serviço para um cliente. A amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), com algum código adicional adicionado ao serviço para converter uma exceção interna a uma falha. O cliente tenta executar a divisão por zero para forçar uma condição de erro no serviço.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 O contrato da calculadora foi <xref:System.ServiceModel.FaultContractAttribute> modificado para incluir um como mostrado no código de amostra a seguir.  
  
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
  
 O <xref:System.ServiceModel.FaultContractAttribute> atributo `Divide` indica que a operação `MathFault`pode retornar uma falha do tipo . Uma falha pode ser de qualquer tipo que possa ser serializada. Neste caso, `MathFault` é um contrato de dados, como segue:  
  
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
  
 O `Divide` método <xref:System.ServiceModel.FaultException%601> lança uma exceção quando uma divisão por exceção zero ocorre como mostrado no código de amostra a seguir. Essa exceção resulta em uma falha sendo enviada ao cliente.  
  
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
  
 O código do cliente força um erro solicitando uma divisão por zero. Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Você vê a divisão por zero sendo relatada como uma falha. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 O cliente faz isso `FaultException<MathFault>` pegando a exceção apropriada:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Por padrão, os detalhes de exceções inesperadas não são enviados ao cliente para evitar que detalhes da implementação do serviço escapem do limite seguro do serviço. `FaultContract`fornece uma maneira de descrever falhas em um contrato e marcar certos tipos de exceções conforme apropriado para transmissão ao cliente. `FaultException<T>`fornece o mecanismo de tempo de execução para o envio de falhas aos consumidores.  
  
 No entanto, é útil ver os detalhes internos de uma falha de serviço ao depurar. Para desativar o comportamento seguro descrito anteriormente, você pode indicar que os detalhes de cada exceção não tratada no servidor devem ser incluídos na falha enviada ao cliente. Isso é feito <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> `true`definindo para . Você pode defini-lo em código ou na configuração, como mostrado na amostra a seguir.  
  
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
  
 Além disso, o comportamento deve ser `behaviorConfiguration` associado ao serviço definindo o atributo do serviço no arquivo de configuração para "CalculadoraServiceBehavior".  
  
 Para pegar tais falhas no cliente, <xref:System.ServiceModel.FaultException> o não genérico deve ser pego.  
  
 Esse comportamento só deve ser utilizado para fins de depuração e nunca deve ser habilitado na produção.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
