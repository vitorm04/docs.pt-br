---
title: Session
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183360"
---
# <a name="session"></a>Session
A amostra de Sessão demonstra como implementar um contrato que requer uma sessão. Uma sessão fornece contexto para a realização de múltiplas operações. Isso permite que um serviço associe o estado a uma determinada sessão, de tal forma que as operações subsequentes possam usar o estado de uma operação anterior. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora. O `ICalculator` contrato foi modificado para permitir que um conjunto de operações aritméticas seja realizado, mantendo um resultado em execução. Essa funcionalidade é definida `ICalculatorSession` pelo contrato. O serviço mantém o estado para um cliente, pois várias operações de serviço são chamadas para realizar um cálculo. O cliente pode recuperar o `Result()` resultado atual ligando `Clear()`e limpar o resultado para zero ligando .  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Definir <xref:System.ServiceModel.SessionMode> o contrato `Required` para garantir que, quando o contrato estiver exposto sobre uma ligação específica, a vinculação suporta sessões. Se a vinculação não suportar sessões, uma exceção será lançada. A `ICalculatorSession` interface é definida de forma que uma ou mais operações possam ser chamadas, o que modifica um resultado em execução, como mostrado no código de amostra a seguir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 O serviço <xref:System.ServiceModel.InstanceContextMode> usa <xref:System.ServiceModel.InstanceContextMode.PerSession> um de para vincular um determinado contexto de instância de serviço a cada sessão recebida. Isso permite que o serviço mantenha o resultado de execução de cada sessão em uma variável de membro local.  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 Quando você executa a amostra, o cliente faz várias solicitações ao servidor e solicita o resultado, que ele exibe na janela do console cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
