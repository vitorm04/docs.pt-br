---
title: "Prevenindo ataques por repetição quando um serviço do WCF é hospedado em uma Web Farm"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4ecf37ffb87ddfdd483cebcac3f5892bab43dcd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prevenindo ataques por repetição quando um serviço do WCF é hospedado em uma Web Farm
Quando usar a segurança de mensagem WCF impede ataques por repetição criando um NONCE fora da mensagem de entrada e verificação interna `InMemoryNonceCache` para ver se o NONCE gerado está presente. Se for, a mensagem será descartada como uma reprodução. Quando um serviço WCF é hospedado em um web farm, desde o `InMemoryNonceCache` não é compartilhado entre os nós no farm da web, o serviço está vulnerável a ataques de repetição.  Para atenuar esse cenário WCF 4.5 fornece um ponto de extensibilidade que permite que você implemente seu próprio cache compartilhado de NONCE derivando uma classe da classe abstrata <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>Implementação de NonceCache  
 Para implementar seu próprio cache NONCE compartilhado, derive uma classe de <xref:System.ServiceModel.Security.NonceCache> e substituir o <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> e <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> métodos. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A>verifica se o NONCE especificado existe no cache. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A>tenta adicionar um valor de uso único para o cache. Depois que a classe é implementada, você associá-lo criando uma instância e atribuindo-a para <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> detecção de repetição do lado do cliente e <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> detecção de repetição do lado do servidor. Não há nenhum limite de suporte a configuração para esse recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
