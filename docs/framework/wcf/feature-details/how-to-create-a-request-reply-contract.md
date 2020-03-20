---
title: Como criar um contrato de resposta/solicitação
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185023"
---
# <a name="how-to-create-a-request-reply-contract"></a>Como criar um contrato de resposta/solicitação
Um contrato de solicitação e resposta especifica um método que retorna uma resposta. A resposta deve ser enviada e correlacionada à solicitação nos termos deste contrato. Mesmo que o método`void` não retorne nenhuma `Sub` resposta (em C#, ou a in Visual Basic), a infra-estrutura cria e envia uma mensagem vazia para o chamador. Para evitar o envio de uma mensagem de resposta vazia, use um contrato de mão única para a operação.  
  
### <a name="to-create-a-request-reply-contract"></a>Para criar um contrato de solicitação e resposta  
  
1. Crie uma interface na linguagem de programação de sua escolha.  
  
2. Aplique <xref:System.ServiceModel.ServiceContractAttribute> o atributo na interface.  
  
3. Aplique <xref:System.ServiceModel.OperationContractAttribute> o atributo a cada método que os clientes podem invocar.  
  
4. Opcional. Defina o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> valor `true` da propriedade para evitar o envio de uma mensagem de resposta vazia. Por padrão, todas as operações são contratos de solicitação e resposta.  
  
## <a name="example"></a>Exemplo  
 A amostra a seguir define um contrato `Add` para `Subtract` um serviço de calculadora que fornece e métodos. O `Multiply` método não faz parte do contrato porque <xref:System.ServiceModel.OperationContractAttribute> não é marcado pela classe e por isso não é acessível aos clientes.  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);

    [OperationContract]
    int Subtract(int a, int b);

    int Multiply(int a, int b)
}
```
  
- Para obter mais informações sobre como <xref:System.ServiceModel.OperationContractAttribute> especificar <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> contratos de operação, consulte a classe e o imóvel.  
  
- A aplicação <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> e atributos faz com que a geração automática de definições de contrato de serviço em um documento WSDL (Web Services Description Language, linguagem de descrição de serviços da Web) uma vez que o serviço seja implantado. O documento é baixado `?wsdl` anexando-se ao endereço base HTTP para o serviço. Por exemplo, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.OperationContractAttribute>
- [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Como criar um contrato duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
