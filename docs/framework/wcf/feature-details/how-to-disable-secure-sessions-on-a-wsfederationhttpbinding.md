---
title: 'Como: desabilitar sessões seguras em uma WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972041"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Como: desabilitar sessões seguras em uma WSFederationHttpBinding

Alguns serviços podem exigir credenciais federadas, mas não dar suporte a sessões seguras. Nesse caso, você deve desabilitar o recurso de sessão segura. Ao contrário <xref:System.ServiceModel.WSHttpBinding>do, <xref:System.ServiceModel.WSFederationHttpBinding> a classe não fornece uma maneira de desabilitar sessões seguras ao se comunicar com um serviço. Em vez disso, você deve criar uma associação personalizada que substitua as configurações de sessão segura por uma inicialização.

Este tópico demonstra como modificar os elementos de associação contidos em um <xref:System.ServiceModel.WSFederationHttpBinding> para criar uma associação personalizada. O resultado é idêntico ao <xref:System.ServiceModel.WSFederationHttpBinding> , exceto que ele não usa sessões seguras.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Para criar uma associação federada personalizada sem sessão segura

1. Crie uma instância da <xref:System.ServiceModel.WSFederationHttpBinding> classe de forma imperativa no código ou carregando uma do arquivo de configuração.

2. Clone o <xref:System.ServiceModel.WSFederationHttpBinding> em um <xref:System.ServiceModel.Channels.CustomBinding>.

3. Localize o <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.CustomBinding>no.

4. Localize o <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> <xref:System.ServiceModel.Channels.SecurityBindingElement>no.

5. Substitua o original <xref:System.ServiceModel.Channels.SecurityBindingElement> pelo elemento de associação <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>de segurança de bootstrap do.

## <a name="example"></a>Exemplo

Este exemplo a seguir cria uma associação federada personalizada sem sessão segura.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Compilando o código

- Para compilar o exemplo de código, crie um projeto que referencie o assembly System. ServiceModel. dll.

## <a name="see-also"></a>Consulte também

- [Associações e segurança](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
