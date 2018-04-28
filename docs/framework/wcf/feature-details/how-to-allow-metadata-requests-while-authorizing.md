---
title: Como permitir solicitações de metadados durante a autorização
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
helpviewer_keywords:
- allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b0b331da49fca7be5106610e4b6f144220cc849
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>Como permitir solicitações de metadados durante a autorização
Durante a autorização personalizada, é necessário para permitir que uma solicitação de metadados a serem processadas. O tópico a seguir apresenta as etapas para validar essa solicitação.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] autorização, consulte [autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>Para permitir solicitações de metadados durante a autorização  
  
1.  Criar uma extensão de <xref:System.ServiceModel.ServiceAuthorizationManager> classe.  
  
2.  Substituir o método <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A>. O método retorna `true` ou `false` dependendo se a autorização é permitida. Obter informações sobre o procedimento atual o <xref:System.ServiceModel.OperationContext> passado como um parâmetro para o método.  
  
3.  Em uma substituição, verifique o nome do contrato, namespace e a ação, conforme mostrado no exemplo a seguir. Se as condições forem válidas, em seguida, retornar `true.`  
  
4.  Use o ponto de extensibilidade para empregar a classe. Para obter mais informações, consulte [como: criar um Gerenciador de autorização personalizada para um serviço](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma substituição do <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> método.  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [Autorização](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
