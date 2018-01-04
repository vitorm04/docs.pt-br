---
title: "Como criar um contrato de resposta/solicitação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f86679d38b8d1a1d6443c1aac37cfa75f426e402
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-request-reply-contract"></a>Como criar um contrato de resposta/solicitação
Um contrato de solicitação-resposta especifica um método que retorna uma resposta. A resposta deve ser enviada e correlacionada a solicitação de acordo com os termos deste contrato. Mesmo se o método não retornar nenhuma resposta (`void` em c#, ou um `Sub` no Visual Basic), a infraestrutura cria e envia uma mensagem vazia para o chamador. Para evitar o envio de uma mensagem de resposta vazia, use um contrato unidirecional para a operação.  
  
### <a name="to-create-a-request-reply-contract"></a>Para criar um contrato de solicitação-resposta  
  
1.  Crie uma interface na linguagem de programação de sua escolha.  
  
2.  Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> de atributo para a interface.  
  
3.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada método que os clientes podem chamar.  
  
4.  Opcional. Defina o valor da <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade `true` para evitar o envio de uma mensagem de resposta vazia. Por padrão, todas as operações são contratos de solicitação-resposta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um contrato para um serviço de cálculo que fornece `Add` e `Subtract` métodos. O `Multiply` método não faz parte do contrato porque ele não está marcado pelo <xref:System.ServiceModel.OperationContractAttribute> de classe e não está acessível aos clientes.  
  
```
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
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como especificar contratos de operação, consulte o <xref:System.ServiceModel.OperationContractAttribute> classe e o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> propriedade.  
  
-   Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos faz com que a geração automática de definições de contrato de serviço em um documento WSDL Web Services Description Language () quando o serviço é implantado. O documento é baixado, acrescentando `?wsdl` para HTTP endereço para o serviço de base. Por exemplo, `http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Como criar um contrato duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
