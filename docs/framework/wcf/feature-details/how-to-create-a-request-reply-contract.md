---
title: 'Como: Criar um contrato de solicitação-resposta'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 085514e09eb13676d5c939724071e89535d443f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663603"
---
# <a name="how-to-create-a-request-reply-contract"></a>Como: Criar um contrato de solicitação-resposta
Um contrato de solicitação-resposta especifica um método que retorna uma resposta. A resposta deve ser enviada e correlacionada à solicitação de acordo com os termos deste contrato. Mesmo que o método retorna sem resposta (`void` em c#, ou um `Sub` no Visual Basic), a infraestrutura cria e envia uma mensagem vazia ao chamador. Para evitar o envio de uma mensagem de resposta vazia, use um contrato unidirecional para a operação.  
  
### <a name="to-create-a-request-reply-contract"></a>Para criar um contrato de solicitação-resposta  
  
1.  Crie uma interface na linguagem de programação de sua escolha.  
  
2.  Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> à interface de atributo.  
  
3.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada método que os clientes podem invocar.  
  
4.  Opcional. Defina o valor da <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade para `true` para impedir o envio de uma mensagem de resposta vazia. Por padrão, todas as operações são contratos de solicitação-resposta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um contrato para um serviço de calculadora fornece `Add` e `Subtract` métodos. O `Multiply` método não é parte do contrato, porque ele não está marcado pelo <xref:System.ServiceModel.OperationContractAttribute> de classe e não está acessível aos clientes.  
  
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
  
-   Para obter mais informações sobre como especificar contratos de operação, consulte o <xref:System.ServiceModel.OperationContractAttribute> classe e o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade.  
  
-   Aplicando o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos faz com que a geração automática de definições de contrato de serviço em um documento de descrição linguagem WSDL (Web Services) quando o serviço é implantado. O documento é baixado por meio do acréscimo `?wsdl` endereço para o serviço de base para o HTTP. Por exemplo, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.OperationContractAttribute>
- [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Como: Criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
