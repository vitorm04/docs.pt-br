---
title: Como desabilitar criptografia de assinaturas digitais
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23d950b6fe4b0183e486dcd127b2a49ac70b615a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a>Como desabilitar criptografia de assinaturas digitais
Por padrão, uma mensagem é assinada e a assinatura digital é criptografada. Isso é controlado pela criação de uma associação personalizada com uma instância do <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e configuração de `MessageProtectionOrder` propriedade ou classe a um <xref:System.ServiceModel.Security.MessageProtectionOrder> valor de enumeração. O padrão é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Esse processo consome até 30% mais tempo do que simplesmente assinatura e criptografia com base no tamanho da mensagem geral (quanto menor a mensagem, maior o impacto de desempenho). A desabilitação da criptografia da assinatura, no entanto, pode permitir que um invasor adivinhar o conteúdo da mensagem. Isso é possível porque o elemento de assinatura contém o código de hash do texto sem formatação de todas as partes da mensagem assinada. Por exemplo, embora o corpo da mensagem é criptografado por padrão, a assinatura não criptografada contém o código hash do corpo da mensagem antes da criptografia. Se o conjunto de valores possíveis para a parte assinada e criptografada é pequeno, um invasor consiga deduzir o conteúdo examinando o valor de hash. Criptografando a assinatura atenua esse vetor de ataque.  
  
 Portanto, desabilite a criptografia da assinatura somente quando o valor do conteúdo for baixo ou o conjunto de valores possíveis de conteúdo é grande e não determinísticas, e o ganho de desempenho mais importante do que como reduzir o ataque descrito acima.  
  
> [!NOTE]
>  Se não houver nada na mensagem que é criptografada, o elemento de assinatura não é criptografado, mesmo quando o <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> está definida como <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Esse comportamento ocorre mesmo com associações fornecidas pelo sistema; todas as associações fornecidas pelo sistema que a ordem de proteção de mensagem definida como `SignBeforeEncryptAndEncryptSignature`. No entanto, o WSDL Web Services Description Language () [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a será ainda contêm o `<sp:EncryptSignature>` asserção.  
  
### <a name="to-disable-digital-signing"></a>Para desabilitar a assinatura digital  
  
1.  Criará um <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, consulte [como: criar um personalizado de associação usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Adicione um <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção de associação.  
  
3.  Definir o <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, ou defina o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
## <a name="see-also"></a>Consulte também  
 [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
