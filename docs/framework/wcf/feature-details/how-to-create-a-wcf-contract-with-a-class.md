---
title: 'Como: Criar um contrato do Windows Communication Foundation com uma classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 90661b4e8f13f0aa3e613bd99bf57dfacdc1eeae
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53773608"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Como: Criar um contrato do Windows Communication Foundation com uma classe
É a melhor maneira de criar um contrato do Windows Communication Foundation (WCF) usando uma interface. Para obter mais informações, confira [Como: Definir um contrato de serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Um alternativo, descrito aqui, é criar uma classe e, em seguida, aplicar a <xref:System.ServiceModel.ServiceContractAttribute> diretamente de atributo à classe e o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada um dos métodos na classe que fazem parte do contrato.  
  
> [!WARNING]
>  `[ServiceContract]` e `[ServiceContractAttribute]` fazer a mesma coisa. O mesmo é verdadeiro para `[OperationContract]` e `[OperationContractAttribute]`. Em cada caso, o primeiro é uma abreviação para o último.  
  
 Para obter mais informações sobre contratos de serviço, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Criando um contrato do Windows Communication Foundation com uma classe  
  
1.  Crie uma nova classe usando o Visual Basic, C#, ou qualquer outra linguagem do tempo de execução de linguagem comum.  
  
2.  Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> classe à classe.  
  
3.  Crie métodos na classe.  
  
4.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do contrato de WCF público.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma classe que define um contrato de serviço.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão. Para obter mais informações sobre esse padrão de mensagem, consulte [como: Criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Você também pode criar e usar outros padrões de mensagens, definindo propriedades do atributo. Para obter mais exemplos, consulte [como: Criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: Criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
