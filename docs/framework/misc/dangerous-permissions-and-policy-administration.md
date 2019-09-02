---
title: Permissões perigosas e administração de políticas
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffe4f3e000c80610d5a105dddef90f9cfd51f0dc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205592"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="69bda-102">Permissões perigosas e administração de políticas</span><span class="sxs-lookup"><span data-stu-id="69bda-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="69bda-103">Várias das operações protegidas para as quais a .NET Framework fornece permissões podem potencialmente permitir que o sistema de segurança seja burlado.</span><span class="sxs-lookup"><span data-stu-id="69bda-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="69bda-104">Essas permissões perigosas devem ser fornecidas apenas ao código digno de confiança e, em seguida, somente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="69bda-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="69bda-105">Normalmente, não há nenhuma defesa contra código mal-intencionado se ele receber essas permissões.</span><span class="sxs-lookup"><span data-stu-id="69bda-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69bda-106">No .NET Framework 4, houve alterações importantes na .NET Framework modelo e terminologia de segurança.</span><span class="sxs-lookup"><span data-stu-id="69bda-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="69bda-107">Para obter mais informações sobre essas alterações, consulte [Security Changes](../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="69bda-107">For more information about these changes, see [Security Changes](../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="69bda-108">As permissões perigosas são explicadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="69bda-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="69bda-109">Permissão</span><span class="sxs-lookup"><span data-stu-id="69bda-109">Permission</span></span>|<span data-ttu-id="69bda-110">Risco potencial</span><span class="sxs-lookup"><span data-stu-id="69bda-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="69bda-111">Permite que o código gerenciado chame código não gerenciado, o que geralmente é perigoso.</span><span class="sxs-lookup"><span data-stu-id="69bda-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="69bda-112">Sem a verificação, o código pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="69bda-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="69bda-113">Evidências invalidadas podem enganar a política de segurança.</span><span class="sxs-lookup"><span data-stu-id="69bda-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="69bda-114">A capacidade de modificar a política de segurança pode desabilitar a segurança.</span><span class="sxs-lookup"><span data-stu-id="69bda-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="69bda-115">O uso da serialização pode burlar os mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="69bda-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="69bda-116">Para obter detalhes, consulte [segurança e serialização](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="69bda-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="69bda-117">A capacidade de definir a entidade atual pode enganar a segurança baseada em função.</span><span class="sxs-lookup"><span data-stu-id="69bda-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="69bda-118">A manipulação de threads é perigosa devido ao estado de segurança associado a threads.</span><span class="sxs-lookup"><span data-stu-id="69bda-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="69bda-119">Pode usar membros privados para derrotar os mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="69bda-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69bda-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69bda-120">See also</span></span>

- [<span data-ttu-id="69bda-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="69bda-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
