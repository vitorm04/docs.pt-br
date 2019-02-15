---
title: 'Como: Usar vários Tokens de segurança do mesmo tipo'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: a532d40d8c31894c63a382ecad0cbcf8b42e3a66
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303758"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Como: Usar vários Tokens de segurança do mesmo tipo
-   No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, um token de cliente de mensagem somente deles independente de qualquer tipo. Agora, as mensagens do cliente podem conter vários tokens de um tipo. Este tópico mostra como incluir vários tokens do mesmo tipo em uma mensagem do cliente.  
  
-   Observe que você não pode configurar um serviço dessa maneira: um serviço pode conter apenas um token de suporte.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Para usar vários tokens de segurança do mesmo tipo  
  
1.  Crie uma coleção de elementos de associação vazia a ser preenchido.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Criar uma <xref:System.ServiceModel.Channels.SecurityBindingElement> chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Criar um <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> coleção.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  Adicione tokens SAML à coleção.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Adicionar a coleção para a <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Adicione elementos de associação para a coleção de elementos de associação.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Retorne uma nova associação personalizada criada da coleção do elemento de associação.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Exemplo  
 Este é todo o método descrito pelo procedimento anterior.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
