---
title: 'Como: criar uma identidade principal personalizada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
ms.openlocfilehash: 05a90c4020f225414b21e82684e46b3c2abda010
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797075"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="f8ada-102">Como: criar uma identidade principal personalizada</span><span class="sxs-lookup"><span data-stu-id="f8ada-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="f8ada-103">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é um meio declarativo de controlar o acesso aos métodos de serviço.</span><span class="sxs-lookup"><span data-stu-id="f8ada-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="f8ada-104">Ao usar esse atributo, a <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeração Especifica o modo para executar verificações de autorização.</span><span class="sxs-lookup"><span data-stu-id="f8ada-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="f8ada-105">Quando esse modo é definido como <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, ele permite que o usuário especifique uma classe <xref:System.Security.Principal.IPrincipal> personalizada retornada pela <xref:System.Threading.Thread.CurrentPrincipal%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f8ada-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="f8ada-106">Este tópico ilustra o cenário quando <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> o é usado em combinação com uma política de autorização personalizada e uma entidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="f8ada-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="f8ada-107">Para obter mais informações sobre como <xref:System.Security.Permissions.PrincipalPermissionAttribute>usar o [, consulte Como: Restrinja o acesso com a classe](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.</span><span class="sxs-lookup"><span data-stu-id="f8ada-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8ada-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f8ada-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8ada-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f8ada-109">Compiling the Code</span></span>  
 <span data-ttu-id="f8ada-110">As referências aos seguintes namespaces são necessárias para compilar o código:</span><span class="sxs-lookup"><span data-stu-id="f8ada-110">References to the following namespaces are needed to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.Collections.Generic>  
  
- <xref:System.Security.Permissions>  
  
- <xref:System.Security.Principal>  
  
- <xref:System.Threading>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Description>  
  
- <xref:System.IdentityModel.Claims>  
  
- <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="f8ada-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8ada-111">See also</span></span>

- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="f8ada-112">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="f8ada-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="f8ada-113">Como: Restringir o acesso com a classe PrincipalPermissionattribute</span><span class="sxs-lookup"><span data-stu-id="f8ada-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)
