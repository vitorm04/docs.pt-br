---
title: 'Como: criar um serviço com interface de contrato'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c31a954d659b3f686f8b9780276a4719064e60cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128707"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Como: criar um serviço com interface de contrato
É a maneira preferencial para criar um contrato do Windows Communication Foundation (WCF) usando uma interface. Esse contrato especifica a coleção e a estrutura de mensagens necessária para acessar as operações de ofertas de serviço. Essa interface define os tipos de entrada e saídos, aplicando o <xref:System.ServiceModel.ServiceContractAttribute> classe para a interface e o <xref:System.ServiceModel.OperationContractAttribute> classe para os métodos que você deseja expor.  
  
 Para obter mais informações sobre contratos de serviço, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Criando um contrato WCF com uma interface  
  
1.  Criar uma nova interface usando o Visual Basic, C#, ou qualquer outra linguagem do tempo de execução de linguagem comum.  
  
2.  Aplique a classe <xref:System.ServiceModel.ServiceContractAttribute> à interface.  
  
3.  Defina os métodos na interface.  
  
4.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do contrato de WCF público.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma interface que define um contrato de serviço.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão. Para obter mais informações sobre esse padrão de mensagem, consulte [como: Criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Você também pode criar e usar outros padrões de mensagens, definindo propriedades do atributo. Para ver mais exemplos, confira [Como: Criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: Criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
