---
title: 'Como: desabilitar criptografia de assinaturas digitais'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: 461c5af2c7fbb98486a8decbe4aa998d8d21070d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911171"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Como: desabilitar criptografia de assinaturas digitais
Por padrão, uma mensagem é assinada e a assinatura é criptografada digitalmente. Isso é controlado por meio da criação de uma associação personalizada com uma <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> instância do <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou do e `MessageProtectionOrder` da configuração da propriedade de qualquer <xref:System.ServiceModel.Security.MessageProtectionOrder> classe para um valor de enumeração. O padrão é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Esse processo consome até 30% mais tempo do que simplesmente assinar e criptografar com base no tamanho geral da mensagem (quanto menor a mensagem, maior o impacto no desempenho). No entanto, desabilitar a criptografia da assinatura pode permitir que um invasor Adivinhe o conteúdo da mensagem. Isso é possível porque o elemento Signature contém o código hash do texto sem formatação de todas as partes assinadas na mensagem. Por exemplo, embora o corpo da mensagem seja criptografado por padrão, a assinatura não criptografada contém o código hash do corpo da mensagem antes da criptografia. Se o conjunto de valores possíveis para a parte assinada e criptografada for pequeno, um invasor poderá deduzir o conteúdo examinando o valor de hash. A criptografia da assinatura reduz esse vetor de ataque.  
  
 Portanto, desabilite a criptografia da assinatura somente quando o valor do conteúdo estiver baixo ou o conjunto de possíveis valores de conteúdo for grande e não determinístico e o lucro de desempenho for mais importante do que reduzir o ataque descrito acima.  
  
> [!NOTE]
> Se não houver nada na mensagem criptografada, o elemento Signature não será criptografado, mesmo quando a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> for definida como. <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> Esse comportamento ocorre mesmo com associações fornecidas pelo sistema; todas as associações fornecidas pelo sistema têm a ordem de proteção de mensagem `SignBeforeEncryptAndEncryptSignature`definida como. No entanto, as gerações do WCF WSDL (Web Services Description Language) `<sp:EncryptSignature>` ainda conterá a asserção.  
  
### <a name="to-disable-digital-signing"></a>Para desabilitar a assinatura digital  
  
1. Criará um <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, confira [Como: Crie uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Adicione um <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção de associação.  
  
3. Defina a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> Propriedade como <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>ou defina a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> Propriedade como <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Consulte também

- [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
