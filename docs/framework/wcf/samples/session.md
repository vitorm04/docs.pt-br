---
title: Session
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: ce91adbb5156eef09221a76773e5a9551f0e8440
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517886"
---
# <a name="session"></a>Session
O exemplo sessão demonstra como implementar um contrato que requer uma sessão. Uma sessão fornece contexto para executar várias operações. Isso permite que um serviço associar a uma determinada sessão, de estado, de modo que as operações subsequentes podem usar o estado de uma operação anterior. Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa um serviço de calculadora. O `ICalculator` contrato foi modificado para permitir que um conjunto de operações aritméticas a serem executadas, mantendo um resultado em execução. Essa funcionalidade é definida pelo `ICalculatorSession` contrato. O serviço mantém o estado para um cliente, como várias operações de serviço são chamadas para executar um cálculo. O cliente pode recuperar o resultado atual chamando `Result()` e desmarque o resultado como zero chamando `Clear()`.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Definindo o <xref:System.ServiceModel.SessionMode> do contrato para `Required` garante que quando o contrato é exposto através de uma ligação específica, a associação dá suporte a sessões. Se a associação não dá suporte a sessões de uma exceção é lançada. O `ICalculatorSession` interface é definida, de modo que podem ser chamadas uma ou mais operações, que modifica um resultado de execução, conforme mostrado no código de exemplo a seguir.  
  
```  
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
  
 O serviço usa um <xref:System.ServiceModel.InstanceContextMode> de <xref:System.ServiceModel.InstanceContextMode.PerSession> para associar um contexto de instância de determinado serviço para cada sessão de entrada. Isso permite que o serviço manter o resultado em execução para cada sessão em uma variável de membro local.  
  
```  
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
  
 Quando você executar o exemplo, o cliente faz várias solicitações ao servidor e solicita que os resultados, que então são exibidos na janela do console de cliente. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a>Consulte também
