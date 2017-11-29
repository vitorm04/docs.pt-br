---
title: "Como usar vários tokens de segurança do mesmo tipo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9827d43ba4b0693d16380d93b066948d464bb978
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Como usar vários tokens de segurança do mesmo tipo
-   Em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, um token de mensagem somente um independente do cliente de qualquer tipo determinado. Agora as mensagens de cliente podem conter vários tokens de um tipo. Este tópico mostra como incluir vários tokens do mesmo tipo em uma mensagem do cliente.  
  
-   Observe que você não pode configurar um serviço dessa forma: um serviço pode conter apenas um token de suporte.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Para usar vários tokens de segurança do mesmo tipo  
  
1.  Crie uma coleção de elementos de associação vazio a ser preenchido.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Criar um <xref:System.ServiceModel.Channels.SecurityBindingElement> chamando <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Criar um <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> coleção.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  Adicione tokens SAML à coleção.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Adicionar a coleção para a <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Adicione elementos de associação para a coleção de elementos de associação.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Retorna uma nova associação personalizada criada a partir de coleção de elementos de associação.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Exemplo  
 A seguir está a todo o método descrito pelo procedimento anterior.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de segurança](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
