---
title: 'Como: criar um SecurityBindingElement para um modo de autenticação especificado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 6466d218ca21e7d2ee4f01f079f308348469fd97
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934340"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="12150-102">Como: criar um SecurityBindingElement para um modo de autenticação especificado</span><span class="sxs-lookup"><span data-stu-id="12150-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="12150-103">O Windows Communication Foundation (WCF) fornece vários modos pelos quais os clientes e serviços se autenticam entre si.</span><span class="sxs-lookup"><span data-stu-id="12150-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="12150-104">Você pode criar elementos de associação de segurança para esses modos de autenticação usando métodos estáticos na <xref:System.ServiceModel.Channels.SecurityBindingElement> classe ou por meio da configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="12150-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="12150-105">Para obter mais informações sobre os 18 modos de autenticação, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="12150-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12150-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12150-106">Example</span></span>  
 <span data-ttu-id="12150-107">O exemplo de código a seguir mostra métodos para criar associações para os vários modos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="12150-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12150-108">Depois que uma instância do <xref:System.ServiceModel.Channels.SecurityBindingElement> objeto é criada, várias propriedades são imutáveis, <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> como e <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="12150-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="12150-109">A `set` chamada a essas propriedades não as altera.</span><span class="sxs-lookup"><span data-stu-id="12150-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="12150-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12150-110">See also</span></span>

- [<span data-ttu-id="12150-111">Modos de autenticação de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="12150-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
- [<span data-ttu-id="12150-112">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="12150-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
