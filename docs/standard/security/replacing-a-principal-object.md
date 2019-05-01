---
title: Substituindo um objeto Principal
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f33be207dd6166b16a04844f3d92b6e017d1c7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018782"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="8aa33-102">Substituindo um objeto Principal</span><span class="sxs-lookup"><span data-stu-id="8aa33-102">Replacing a Principal Object</span></span>
<span data-ttu-id="8aa33-103">Aplicativos que fornecem serviços de autenticação devem ser capazes de substituir os **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) para um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="8aa33-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="8aa33-104">Além disso, o sistema de segurança deve ajudar a proteger a capacidade de substituir **Principal** objetos porque um maliciosamente anexado incorreto **Principal** comprometa a segurança do seu aplicativo por reivindicar uma identidade irreais ou função.</span><span class="sxs-lookup"><span data-stu-id="8aa33-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="8aa33-105">Portanto, aplicativos que exigem a capacidade de substituir **Principal** objetos devem ser concedidos a <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objeto para o controle principal.</span><span class="sxs-lookup"><span data-stu-id="8aa33-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="8aa33-106">(Observe que essa permissão não é necessária para realizar verificações de segurança baseada em função ou de criação **Principal** objetos.)</span><span class="sxs-lookup"><span data-stu-id="8aa33-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="8aa33-107">O atual **Principal** objeto pode ser substituído por meio das seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="8aa33-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="8aa33-108">Criar a substituição **Principal** do objeto e associados **identidade** objeto.</span><span class="sxs-lookup"><span data-stu-id="8aa33-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="8aa33-109">Anexar o novo **Principal** objeto para o contexto de chamada.</span><span class="sxs-lookup"><span data-stu-id="8aa33-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aa33-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8aa33-110">Example</span></span>  
 <span data-ttu-id="8aa33-111">O exemplo a seguir mostra como criar um objeto de entidade genérico e usá-lo para definir a entidade de um thread.</span><span class="sxs-lookup"><span data-stu-id="8aa33-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8aa33-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8aa33-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="8aa33-113">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="8aa33-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
