---
title: Substituindo um objeto Principal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="ae096-102">Substituindo um objeto Principal</span><span class="sxs-lookup"><span data-stu-id="ae096-102">Replacing a Principal Object</span></span>
<span data-ttu-id="ae096-103">Aplicativos que fornecem serviços de autenticação devem ser capazes de substituir o **Principal** objeto (<xref:System.Security.Principal.IPrincipal>) para um determinado thread.</span><span class="sxs-lookup"><span data-stu-id="ae096-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="ae096-104">Além disso, o sistema de segurança deve ajudar a proteger a capacidade de substituir **Principal** objetos porque um maliciosamente anexado incorreto **Principal** comprometa a segurança do seu aplicativo reivindicar uma verdade identidade ou uma função.</span><span class="sxs-lookup"><span data-stu-id="ae096-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="ae096-105">Portanto, aplicativos que requerem a capacidade de substituir **Principal** objetos devem ser concedidos a <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objeto de controle principal.</span><span class="sxs-lookup"><span data-stu-id="ae096-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="ae096-106">(Observe que essa permissão não é necessária para executar verificações de segurança baseada em função ou para a criação de **Principal** objetos.)</span><span class="sxs-lookup"><span data-stu-id="ae096-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="ae096-107">Atual **Principal** objeto pode ser substituído por executar as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="ae096-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="ae096-108">Criar a substituição **Principal** do objeto e associados **identidade** objeto.</span><span class="sxs-lookup"><span data-stu-id="ae096-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="ae096-109">Anexar o novo **Principal** objeto para o contexto de chamada.</span><span class="sxs-lookup"><span data-stu-id="ae096-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae096-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae096-110">Example</span></span>  
 <span data-ttu-id="ae096-111">O exemplo a seguir mostra como criar um objeto principal genérico e usá-lo para definir a entidade de um thread.</span><span class="sxs-lookup"><span data-stu-id="ae096-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ae096-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae096-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="ae096-113">Objetos Principal e Identity</span><span class="sxs-lookup"><span data-stu-id="ae096-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
