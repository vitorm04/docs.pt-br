---
title: "Como criar um serviço com interface de contrato"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b00a7cbbab343eb209895affbbbba76ef2af2959
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Como criar um serviço com interface de contrato
A melhor maneira de criar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] contrato é usando uma interface. Esse contrato especifica a coleta e a estrutura de mensagens necessária para acessar as operações de ofertas de serviço. Essa interface define os tipos de entrada e saídos aplicando o <xref:System.ServiceModel.ServiceContractAttribute> classe para a interface e o <xref:System.ServiceModel.OperationContractAttribute> classe para os métodos que você deseja expor.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contratos de serviço, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Criando um contrato WCF com uma interface  
  
1.  Criar uma nova interface usando [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], c# ou qualquer outra linguagem common language runtime.  
  
2.  Aplique a classe <xref:System.ServiceModel.ServiceContractAttribute> à interface.  
  
3.  Defina os métodos na interface.  
  
4.  Aplicar o <xref:System.ServiceModel.OperationContractAttribute> classe para cada método que deve ser exposto como parte do público [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra uma interface que define um contrato de serviço.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Os métodos que têm o <xref:System.ServiceModel.OperationContractAttribute> classe aplicada usam um padrão de mensagem de solicitação-resposta por padrão. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Esse padrão de mensagem, consulte [como: criar um contrato de solicitação-resposta](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Você também pode criar e usar outros padrões de mensagem definindo propriedades do atributo. Para obter mais exemplos, consulte [como: criar um contrato unidirecional](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) e [como: criar um contrato Duplex](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
