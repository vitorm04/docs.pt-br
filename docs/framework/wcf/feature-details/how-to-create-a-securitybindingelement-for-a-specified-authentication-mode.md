---
title: "Como criar um SecurityBindingElement para um modo de autenticação especificado"
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
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 658eaf3469e0be179c78d9963687e6de9cb7fc00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="468fa-102">Como criar um SecurityBindingElement para um modo de autenticação especificado</span><span class="sxs-lookup"><span data-stu-id="468fa-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="468fa-103">fornece vários modos pelos quais os clientes e serviços autenticam um ao outro.</span><span class="sxs-lookup"><span data-stu-id="468fa-103"> provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="468fa-104">Você pode criar elementos de associação para esses modos de autenticação de segurança usando os métodos estáticos no <xref:System.ServiceModel.Channels.SecurityBindingElement> classe ou por meio de configuração, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="468fa-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="468fa-105">os modos de 18 autenticação, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span><span class="sxs-lookup"><span data-stu-id="468fa-105"> the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="468fa-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="468fa-106">Example</span></span>  
 <span data-ttu-id="468fa-107">O exemplo de código a seguir mostra os métodos para criação de associações para diversos modos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="468fa-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="468fa-108">Uma vez em uma instância do <xref:System.ServiceModel.Channels.SecurityBindingElement> objeto é criado, um número de propriedades é imutável, como <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> e <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="468fa-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="468fa-109">Chamando `set` essas propriedades não alterá-los.</span><span class="sxs-lookup"><span data-stu-id="468fa-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="468fa-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="468fa-110">See Also</span></span>  
 [<span data-ttu-id="468fa-111">Modos de autenticação SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="468fa-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [<span data-ttu-id="468fa-112">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="468fa-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
