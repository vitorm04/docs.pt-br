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
ms.openlocfilehash: ae24cdcb97e30da0bd4aec6569ef3dcda11488c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078936"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="3369f-102">Permissões perigosas e administração de políticas</span><span class="sxs-lookup"><span data-stu-id="3369f-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="3369f-103">Várias operações protegidas para o qual o .NET Framework fornece permissões potencialmente podem permitir que o sistema de segurança seja contornado.</span><span class="sxs-lookup"><span data-stu-id="3369f-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="3369f-104">Essas permissões perigosas devem ser dada apenas ao código confiável e, em seguida, somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="3369f-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="3369f-105">Normalmente, há nenhuma defesa contra código mal-intencionado se ele tem essas permissões.</span><span class="sxs-lookup"><span data-stu-id="3369f-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3369f-106">No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], houve alterações importantes para o modelo de segurança do .NET Framework e a terminologia.</span><span class="sxs-lookup"><span data-stu-id="3369f-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="3369f-107">Para obter mais informações sobre essas alterações, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="3369f-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="3369f-108">Permissões perigosas são explicadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3369f-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="3369f-109">Permissão</span><span class="sxs-lookup"><span data-stu-id="3369f-109">Permission</span></span>|<span data-ttu-id="3369f-110">Risco em potencial</span><span class="sxs-lookup"><span data-stu-id="3369f-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="3369f-111">Permite que o código gerenciado chamar código não gerenciado, que geralmente é perigoso.</span><span class="sxs-lookup"><span data-stu-id="3369f-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="3369f-112">Sem a verificação, o código pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="3369f-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="3369f-113">Evidência invalidada pode enganar a diretiva de segurança.</span><span class="sxs-lookup"><span data-stu-id="3369f-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="3369f-114">A capacidade de modificar a política de segurança pode desativar a segurança.</span><span class="sxs-lookup"><span data-stu-id="3369f-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="3369f-115">O uso da serialização pode desviar os mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="3369f-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="3369f-116">Para obter detalhes, consulte [segurança e serialização](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="3369f-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="3369f-117">A capacidade de definir a atual entidade pode enganar segurança baseada em função.</span><span class="sxs-lookup"><span data-stu-id="3369f-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="3369f-118">Manipulação de threads é perigosa devido ao estado de segurança associado a threads.</span><span class="sxs-lookup"><span data-stu-id="3369f-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="3369f-119">Pode usar membros particulares para anular os mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="3369f-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3369f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3369f-120">See also</span></span>

- [<span data-ttu-id="3369f-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="3369f-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
