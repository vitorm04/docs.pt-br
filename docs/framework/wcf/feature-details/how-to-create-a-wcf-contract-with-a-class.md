---
title: Como criar um contrato do Windows Communication Foundation com uma classe
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa09e1900b0709130cb4c58240c38d1bd5d1d92d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Como criar um contrato do Windows Communication Foundation com uma classe
A melhor maneira de criar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contrato é usando uma interface. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Como: definir um contrato de serviço](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Uma alternativa, descrito aqui, é criar uma classe e, em seguida, aplicar o <xref:System.ServiceModel.ServiceContractAttribute> diretamente de atributo para a classe e o <xref:System.ServiceModel.OperationContractAttribute> de atributo para cada um dos métodos na classe que fazem parte do contrato.  
  
> [!WARNING]
>  `[ServiceContract]` e `[ServiceContractAttribute]` fazer a mesma coisa. A mesma coisa que ele true para `[OperationContract]` e `[OperationContractAttribute]`. Em cada caso o anterior é abreviado para o último.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] contratos de serviço, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Criar um contrato do Windows Communication Foundation com uma classe  
  
1.  Crie uma nova classe usando o Visual Basic, c# ou qualquer outra linguagem common language runtime.  
  
2.  Aplicar o <xref:System.ServiceModel.ServiceContractAttribute> classe para a classe.  
  
3.  Crie métodos na classe.  
  
4.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do público [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma classe que define um contrato de serviço.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Esse padrão de mensagem, consulte [como: criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Você também pode criar e usar outros padrões de mensagem definindo propriedades do atributo. Para obter mais exemplos, consulte [como: criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
