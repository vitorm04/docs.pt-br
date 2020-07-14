---
title: Permissões perigosas e administração de políticas
description: Consulte links para as várias permissões perigosas no .NET. Essas permissões devem ser fornecidas somente para código confiável e somente quando necessário.
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: ba3d47dc445e4b368f57d59d735fc331f5d6de81
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281609"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="4054b-104">Permissões perigosas e administração de políticas</span><span class="sxs-lookup"><span data-stu-id="4054b-104">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="4054b-105">Várias das operações protegidas para as quais a .NET Framework fornece permissões podem potencialmente permitir que o sistema de segurança seja burlado.</span><span class="sxs-lookup"><span data-stu-id="4054b-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="4054b-106">Essas permissões perigosas devem ser fornecidas apenas ao código digno de confiança e, em seguida, somente conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="4054b-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="4054b-107">Normalmente, não há nenhuma defesa contra código mal-intencionado se ele receber essas permissões.</span><span class="sxs-lookup"><span data-stu-id="4054b-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4054b-108">No .NET Framework 4, houve alterações importantes na .NET Framework modelo e terminologia de segurança.</span><span class="sxs-lookup"><span data-stu-id="4054b-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="4054b-109">Para obter mais informações sobre essas alterações, consulte [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="4054b-109">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="4054b-110">As permissões perigosas são explicadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4054b-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="4054b-111">Permissão</span><span class="sxs-lookup"><span data-stu-id="4054b-111">Permission</span></span>|<span data-ttu-id="4054b-112">Risco potencial</span><span class="sxs-lookup"><span data-stu-id="4054b-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="4054b-113">Permite que o código gerenciado chame código não gerenciado, o que geralmente é perigoso.</span><span class="sxs-lookup"><span data-stu-id="4054b-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="4054b-114">Sem a verificação, o código pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="4054b-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="4054b-115">Evidências invalidadas podem enganar a política de segurança.</span><span class="sxs-lookup"><span data-stu-id="4054b-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="4054b-116">A capacidade de modificar a política de segurança pode desabilitar a segurança.</span><span class="sxs-lookup"><span data-stu-id="4054b-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="4054b-117">O uso da serialização pode burlar os mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="4054b-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="4054b-118">Para obter detalhes, consulte [segurança e serialização](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="4054b-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="4054b-119">A capacidade de definir a entidade atual pode enganar a segurança baseada em função.</span><span class="sxs-lookup"><span data-stu-id="4054b-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="4054b-120">A manipulação de threads é perigosa devido ao estado de segurança associado a threads.</span><span class="sxs-lookup"><span data-stu-id="4054b-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="4054b-121">Pode usar membros privados para derrotar os mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="4054b-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4054b-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="4054b-122">See also</span></span>

- [<span data-ttu-id="4054b-123">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="4054b-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
