---
title: Substituindo um objeto Principal
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: fced91aef991bc228e65128d5e8d69e6a46588e5
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557093"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="ef07c-102">Substituindo um objeto Principal</span><span class="sxs-lookup"><span data-stu-id="ef07c-102">Replacing a Principal Object</span></span>

<span data-ttu-id="ef07c-103">Os aplicativos que fornecem serviços de autenticação devem ser capazes de substituir o objeto **principal** ( <xref:System.Security.Principal.IPrincipal> ) para um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="ef07c-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="ef07c-104">Além disso, o sistema de segurança deve ajudar a proteger a capacidade de substituir os objetos **principais** , pois uma **entidade** de segurança incorreta, comprometida de forma mal-intencionada, compromete o seu aplicativo reivindicando uma identidade ou função inverdadeira.</span><span class="sxs-lookup"><span data-stu-id="ef07c-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="ef07c-105">Portanto, os aplicativos que exigem a capacidade de substituir objetos de **entidade** devem receber o <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objeto para o controle principal.</span><span class="sxs-lookup"><span data-stu-id="ef07c-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="ef07c-106">(Observe que essa permissão não é necessária para executar verificações de segurança baseadas em função ou para a criação de objetos **principal** .)</span><span class="sxs-lookup"><span data-stu-id="ef07c-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="ef07c-107">O objeto **principal** atual pode ser substituído executando as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ef07c-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="ef07c-108">Crie o objeto **principal** de substituição e o objeto de **identidade** associado.</span><span class="sxs-lookup"><span data-stu-id="ef07c-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="ef07c-109">Anexe o novo objeto **principal** ao contexto de chamada.</span><span class="sxs-lookup"><span data-stu-id="ef07c-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef07c-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef07c-110">Example</span></span>

<span data-ttu-id="ef07c-111">O exemplo a seguir mostra como criar um objeto principal genérico e usá-lo para definir a entidade de segurança de um thread.</span><span class="sxs-lookup"><span data-stu-id="ef07c-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ef07c-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="ef07c-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="ef07c-113">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="ef07c-113">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="ef07c-114">Segurança de ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ef07c-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
