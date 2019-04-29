---
title: 'Como: desabilitar criptografia de assinaturas digitais'
ms.date: 03/30/2017
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
ms.openlocfilehash: e2fd2a058e636ebf398f9d0c71a93788ccd7dfa0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773185"
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Como: desabilitar criptografia de assinaturas digitais
Por padrão, uma mensagem é assinada e a assinatura digital é criptografada. Isso é controlado pela criação de uma associação personalizada com uma instância da <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e definindo o `MessageProtectionOrder` propriedade de qualquer classe para um <xref:System.ServiceModel.Security.MessageProtectionOrder> valor de enumeração. O padrão é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Esse processo consome até 30 por cento mais tempo do que simplesmente assinar e criptografar com base no tamanho geral da mensagem (a mensagem menor, maior o impacto de desempenho). Desabilitar a criptografia da assinatura, no entanto, pode permitir que um invasor adivinhar o conteúdo da mensagem. Isso é possível porque o elemento de assinatura contém o código hash do texto sem formatação de todas as partes na mensagem assinada. Por exemplo, embora o corpo da mensagem é criptografado por padrão, a assinatura não criptografada contém o código hash do corpo da mensagem antes da criptografia. Se o conjunto de valores possíveis para a parte assinado e criptografado é pequeno, um invasor poderá deduzir o conteúdo, observando o valor de hash. Criptografando a assinatura atenua esse vetor de ataque.  
  
 Portanto, desabilite a criptografia da assinatura somente quando o valor do conteúdo é baixo ou o conjunto de valores possíveis de conteúdo é grande e não determinísticas, e o ganho de desempenho é mais importante do que reduzir o ataque descrito acima.  
  
> [!NOTE]
>  Se não houver nada na mensagem que é criptografada, o elemento de assinatura não for criptografado, mesmo quando o <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> estiver definida como <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Esse comportamento ocorre mesmo com associações fornecidas pelo sistema; todas as associações fornecidas pelo sistema que a ordem de proteção de mensagem definida como `SignBeforeEncryptAndEncryptSignature`. No entanto, a descrição de linguagem WSDL (Web Services) WCF gera será ainda contêm a `<sp:EncryptSignature>` asserção.  
  
### <a name="to-disable-digital-signing"></a>Para desabilitar a assinatura digital  
  
1. Criará um <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, confira [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2. Adicione uma <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção de associação.  
  
3. Defina a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, ou defina o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Consulte também

- [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
