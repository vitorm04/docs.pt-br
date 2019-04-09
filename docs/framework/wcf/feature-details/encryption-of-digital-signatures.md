---
title: Criptografia de assinaturas digitais
ms.date: 03/30/2017
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
ms.openlocfilehash: ac3df9c08462b6421a0549c5927512586abf303a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134570"
---
# <a name="encryption-of-digital-signatures"></a>Criptografia de assinaturas digitais
Por padrão, uma mensagem foi assinada e criptografada e a assinatura digital é criptografada. Você pode controlar isso criando uma associação personalizada com uma instância das <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e, em seguida, definindo o `MessageProtectionOrder` propriedade de qualquer classe para um <xref:System.ServiceModel.Security.MessageProtectionOrder> valor de enumeração. O padrão é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>. Esse processo leva de 10 a 40 por cento de mais de simplesmente assinar e criptografar. Desabilitar a criptografia da assinatura, no entanto, pode permitir que um invasor adivinhar o conteúdo da mensagem. Isso é possível porque o elemento de assinatura contém o código hash do texto sem formatação de todas as partes na mensagem assinada. Por exemplo, embora o corpo da mensagem é criptografado por padrão, a assinatura não criptografada contém o código hash do corpo da mensagem. Se a mensagem for pequena, um invasor poderá deduzir o conteúdo. Criptografando a assinatura reduz ou elimina essa possibilidade.  
  
 Portanto, desabilite a criptografia da assinatura somente quando o valor do conteúdo é baixo, e o ganho de desempenho será significativo, por exemplo, ao enviar os arquivos binários grandes que têm sem implicações de segurança.  
  
### <a name="to-disable-digital-signing"></a>Para desabilitar a assinatura digital  
  
1.  Criará um <xref:System.ServiceModel.Channels.CustomBinding>. Para obter mais informações, confira [Como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
2.  Adicione uma <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção de associação.  
  
3.  Defina a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, ou defina o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.  
  
 Para obter mais informações sobre como criar associações personalizadas, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Para obter mais informações sobre como criar uma ligação personalizada para um modo de autenticação específicos, consulte [como: Criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Security.MessageProtectionOrder>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Criando associações definidas pelo usuário](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Como: criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
