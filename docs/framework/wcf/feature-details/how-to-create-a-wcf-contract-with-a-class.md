---
title: 'Como: Criar um contrato de Windows Communication Foundation com uma classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988747"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Como: Criar um contrato de Windows Communication Foundation com uma classe
A maneira preferida de criar um contrato de Windows Communication Foundation (WCF) é usando uma interface. Para obter mais informações, confira [Como: Defina um contrato](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)de serviço. Uma alternativa, descrita aqui, é criar uma classe e, em seguida, aplicar o <xref:System.ServiceModel.ServiceContractAttribute> atributo à classe diretamente e o <xref:System.ServiceModel.OperationContractAttribute> atributo a cada um dos métodos na classe que fazem parte do contrato.  
  
> [!WARNING]
> `[ServiceContract]`e `[ServiceContractAttribute]` fazer a mesma coisa. A mesma coisa é verdadeira para `[OperationContract]` e `[OperationContractAttribute]`. Em cada caso, a primeira é a abreviação do último.  
  
 Para obter mais informações sobre contratos de serviço, consulte [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Criando um contrato de Windows Communication Foundation com uma classe  
  
1. Crie uma nova classe usando Visual Basic, C#ou qualquer outra linguagem de Common Language Runtime.  
  
2. Aplique a <xref:System.ServiceModel.ServiceContractAttribute> classe à classe.  
  
3. Crie métodos na classe.  
  
4. Aplique a <xref:System.ServiceModel.OperationContractAttribute> classe a cada método que deve ser exposto como parte do contrato do WCF público.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma classe que define um contrato de serviço.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Por padrão, os métodos <xref:System.ServiceModel.OperationContractAttribute> que têm a classe aplicada usam um padrão de mensagem de solicitação-resposta. Para obter mais informações sobre esse padrão de mensagem [, consulte Como: Crie um contrato](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)de solicitação-resposta. Você também pode criar e usar outros padrões de mensagem definindo as propriedades do atributo. Para ver mais exemplos, confira [Como: Crie um contrato](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) unidirecional e [como: Crie um contrato](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)duplex.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
