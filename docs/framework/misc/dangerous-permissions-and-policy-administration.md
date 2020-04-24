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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645755"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="cb7a7-102">Permissões perigosas e administração de políticas</span><span class="sxs-lookup"><span data-stu-id="cb7a7-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="cb7a7-103">Várias das operações protegidas para as quais o .NET Framework fornece permissões podem potencialmente permitir que o sistema de segurança seja contornado.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="cb7a7-104">Essas permissões perigosas devem ser dadas apenas a códigos confiáveis, e então apenas quando necessário.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="cb7a7-105">Geralmente não há defesa contra código malicioso se for concedida essas permissões.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb7a7-106">No Quadro .NET 4, houve mudanças importantes no modelo de segurança e terminologia do Quadro .NET.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="cb7a7-107">Para obter mais informações sobre essas alterações, consulte [Alterações de segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="cb7a7-107">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="cb7a7-108">As permissões perigosas são explicadas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="cb7a7-109">Permissão</span><span class="sxs-lookup"><span data-stu-id="cb7a7-109">Permission</span></span>|<span data-ttu-id="cb7a7-110">Risco potencial</span><span class="sxs-lookup"><span data-stu-id="cb7a7-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="cb7a7-111">Permite que o código gerenciado seja chamado em código não gerenciado, o que muitas vezes é perigoso.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="cb7a7-112">Sem verificação, o código pode fazer qualquer coisa.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="cb7a7-113">Evidências invalidadas podem enganar a política de segurança.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="cb7a7-114">A capacidade de modificar a política de segurança pode desativar a segurança.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="cb7a7-115">O uso da serialização pode contornar mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="cb7a7-116">Para obter detalhes, consulte [Segurança e Serialização](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="cb7a7-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="cb7a7-117">A capacidade de definir o principal atual pode enganar a segurança baseada em papéis.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="cb7a7-118">A manipulação de fios é perigosa por causa do estado de segurança associado aos segmentos.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="cb7a7-119">Pode usar membros privados para derrotar mecanismos de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="cb7a7-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb7a7-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb7a7-120">See also</span></span>

- [<span data-ttu-id="cb7a7-121">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="cb7a7-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
