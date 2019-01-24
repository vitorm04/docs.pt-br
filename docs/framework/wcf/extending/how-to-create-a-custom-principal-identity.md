---
title: 'Como: Criar uma identidade de entidade de segurança personalizada'
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
ms.openlocfilehash: 8f957419bcb12b0dbe735240df3cd38fa7d16e76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739674"
---
# <a name="how-to-create-a-custom-principal-identity"></a><span data-ttu-id="13a85-102">Como: Criar uma identidade de entidade de segurança personalizada</span><span class="sxs-lookup"><span data-stu-id="13a85-102">How to: Create a Custom Principal Identity</span></span>
<span data-ttu-id="13a85-103">O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é uma forma declarativa de controlar o acesso aos métodos de serviço.</span><span class="sxs-lookup"><span data-stu-id="13a85-103">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is a declarative means of controlling access to service methods.</span></span> <span data-ttu-id="13a85-104">Ao usar esse atributo, o <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeração Especifica o modo para realizar verificações de autorização.</span><span class="sxs-lookup"><span data-stu-id="13a85-104">When using this attribute, the <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeration specifies the mode for performing authorization checks.</span></span> <span data-ttu-id="13a85-105">Quando esse modo é definido como <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, ele permite que o usuário especifique um personalizado <xref:System.Security.Principal.IPrincipal> classe retornado pelo <xref:System.Threading.Thread.CurrentPrincipal%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="13a85-105">When this mode is set to <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, it enables the user to specify a custom <xref:System.Security.Principal.IPrincipal> class returned by the <xref:System.Threading.Thread.CurrentPrincipal%2A> property.</span></span> <span data-ttu-id="13a85-106">Este tópico ilustra o cenário quando <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> é usado em combinação com uma política de autorização personalizada e uma entidade personalizada.</span><span class="sxs-lookup"><span data-stu-id="13a85-106">This topic illustrates the scenario when <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> is used in combination with a custom authorization policy and a custom principal.</span></span>  
  
 <span data-ttu-id="13a85-107">Para obter mais informações sobre como usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute>, consulte [como: Restringir o acesso com a classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="13a85-107">For more information about using the <xref:System.Security.Permissions.PrincipalPermissionAttribute>, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a85-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13a85-108">Example</span></span>  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13a85-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="13a85-109">Compiling the Code</span></span>  
 <span data-ttu-id="13a85-110">Referências aos namespaces a seguir são necessários para compilar o código:</span><span class="sxs-lookup"><span data-stu-id="13a85-110">References to the following namespaces are needed to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a><span data-ttu-id="13a85-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13a85-111">See also</span></span>
- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.ServiceModel.Description.PrincipalPermissionMode>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [<span data-ttu-id="13a85-112">Como: Usar o provedor de função ASP.NET com um serviço</span><span class="sxs-lookup"><span data-stu-id="13a85-112">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="13a85-113">Como: Restringir o acesso com a PrincipalPermissionAttribute Class</span><span class="sxs-lookup"><span data-stu-id="13a85-113">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
