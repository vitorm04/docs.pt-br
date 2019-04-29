---
title: Prevenindo ataques por repetição quando um serviço do WCF é hospedado em uma Web Farm
ms.date: 03/30/2017
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
ms.openlocfilehash: e27a85d42268df107b26d3bd24af15a639bb1836
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641587"
---
# <a name="preventing-replay-attacks-when-a-wcf-service-is-hosted-in-a-web-farm"></a>Prevenindo ataques por repetição quando um serviço do WCF é hospedado em uma Web Farm
Quando usando a segurança de mensagem WCF impede ataques de reprodução, criando um NONCE fora a mensagem de entrada e verificação interna `InMemoryNonceCache` para ver se o NONCE gerado está presente. Se for, a mensagem é descartada como uma reprodução. Quando um serviço WCF está hospedado em um web farm, desde o `InMemoryNonceCache` não é compartilhado entre os nós no farm da web, o serviço está vulnerável a ataques de repetição.  Para reduzir esse cenário WCF 4.5 fornece um ponto de extensibilidade que permite que você implemente seu próprio cache NONCE compartilhado derivando uma classe da classe abstrata <xref:System.ServiceModel.Security.NonceCache>.  
  
## <a name="noncecache-implementation"></a>Implementação de NonceCache  
 Para implementar seu próprio cache NONCE compartilhado, derive uma classe de <xref:System.ServiceModel.Security.NonceCache> e substitua o <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> e <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> métodos. <xref:System.ServiceModel.Security.NonceCache.CheckNonce%2A> verifica se o NONCE especificado existe no cache. <xref:System.ServiceModel.Security.NonceCache.TryAddNonce%2A> tenta adicionar um NONCE ao cache. Depois que a classe é implementada, você conectá-la ao instanciar uma instância e atribuí-lo à <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.NonceCache%2A> detecção de reprodução para o lado do cliente e <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NonceCache%2A> para o lado do servidor de detecção de reprodução. Não há nenhum limite de suporte para esse recurso de configuração.  
  
## <a name="see-also"></a>Consulte também

- [Segurança de mensagem](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)
