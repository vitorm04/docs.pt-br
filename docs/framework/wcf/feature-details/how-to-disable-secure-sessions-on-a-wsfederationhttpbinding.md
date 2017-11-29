---
title: "Como desabilitar sessões seguranças em uma WSFederationHttpBinding"
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
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bb2970209814fbbee9f71f0263a4d3d4f02f3e20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Como desabilitar sessões seguranças em uma WSFederationHttpBinding
Alguns serviços podem exigir credenciais federadas mas não oferecer suporte a sessões seguras. Nesse caso, você deve desabilitar o recurso de sessão segura. Ao contrário de <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, a <xref:System.ServiceModel.WSFederationHttpBinding> classe não fornecerá uma maneira de desabilitar sessões seguras ao se comunicar com um serviço. Em vez disso, você deve criar uma associação personalizada que substitui as configurações de sessão segura com um programa de inicialização.  
  
 Este tópico demonstra como modificar os elementos de associação contidos em um <xref:System.ServiceModel.WSFederationHttpBinding> para criar uma associação personalizada. O resultado é idêntico de <xref:System.ServiceModel.WSFederationHttpBinding> exceto que não usa sessões seguras.  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Para criar um personalizado federado associação sem sessão segura  
  
1.  Criar uma instância do <xref:System.ServiceModel.WSFederationHttpBinding> classe imperativa no código ou carregando um arquivo de configuração.  
  
2.  Clone o <xref:System.ServiceModel.WSFederationHttpBinding> em um <xref:System.ServiceModel.Channels.CustomBinding>.  
  
3.  Localizar o <xref:System.ServiceModel.Channels.SecurityBindingElement> no <xref:System.ServiceModel.Channels.CustomBinding>.  
  
4.  Localizar o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> no <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
5.  Substituir o original <xref:System.ServiceModel.Channels.SecurityBindingElement> com o elemento de associação de segurança de inicialização de <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo a seguir cria uma associação personalizada federada sem sessão segura.  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar o exemplo de código, crie um projeto que referencia o assembly System.ServiceModel.dll.  
  
## <a name="see-also"></a>Consulte também  
 [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
