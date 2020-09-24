---
title: Permissão de segurança para redirecionamento de associações de assemblies
description: Saiba mais sobre a permissão de segurança necessária para redirecionamento de associação de assembly explícita em um arquivo de configuração de aplicativo no .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: 2de2c50f5adb9e9fa36ea015ef498e9953c83005
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165215"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="a285f-103">Permissão de segurança para redirecionamento de associações de assemblies</span><span class="sxs-lookup"><span data-stu-id="a285f-103">Assembly Binding Redirection Security Permission</span></span>

<span data-ttu-id="a285f-104">O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança.</span><span class="sxs-lookup"><span data-stu-id="a285f-104">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="a285f-105">Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="a285f-105">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="a285f-106">A permissão é concedida definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="a285f-106">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a285f-107">Os assemblies gerenciados não têm permissões por padrão.</span><span class="sxs-lookup"><span data-stu-id="a285f-107">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="a285f-108">A permissão de segurança é concedida a aplicativos executados na zona de zona confiável (computador local) e na intranet.</span><span class="sxs-lookup"><span data-stu-id="a285f-108">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="a285f-109">Os aplicativos executados na zona da Internet são estritamente proibidos de executar o redirecionamento de associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="a285f-109">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="a285f-110">A permissão não será necessária se o redirecionamento de assembly for executado em um arquivo de política do Publicador que é controlado pelo editor de componentes ou no arquivo de configuração do computador que é controlado pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="a285f-110">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="a285f-111">No entanto, a permissão é necessária para que um aplicativo ignore explicitamente a política do editor usando o [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a285f-111">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="a285f-112">A tabela a seguir mostra as configurações de segurança padrão para o sinalizador **BindingRedirects** .</span><span class="sxs-lookup"><span data-stu-id="a285f-112">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="a285f-113">Zona</span><span class="sxs-lookup"><span data-stu-id="a285f-113">Zone</span></span>|<span data-ttu-id="a285f-114">Configuração do sinalizador BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="a285f-114">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="a285f-115">Zona confiável (computador local)</span><span class="sxs-lookup"><span data-stu-id="a285f-115">Trusted Zone (local machine)</span></span>|<span data-ttu-id="a285f-116">**ON**</span><span class="sxs-lookup"><span data-stu-id="a285f-116">**ON**</span></span>|  
|<span data-ttu-id="a285f-117">Zona da Intranet</span><span class="sxs-lookup"><span data-stu-id="a285f-117">Intranet Zone</span></span>|<span data-ttu-id="a285f-118">**ON**</span><span class="sxs-lookup"><span data-stu-id="a285f-118">**ON**</span></span>|  
|<span data-ttu-id="a285f-119">Zona da Internet</span><span class="sxs-lookup"><span data-stu-id="a285f-119">Internet Zone</span></span>|<span data-ttu-id="a285f-120">**OFF**</span><span class="sxs-lookup"><span data-stu-id="a285f-120">**OFF**</span></span>|  
|<span data-ttu-id="a285f-121">Zonas não confiáveis</span><span class="sxs-lookup"><span data-stu-id="a285f-121">Untrusted zones</span></span>|<span data-ttu-id="a285f-122">**OFF**</span><span class="sxs-lookup"><span data-stu-id="a285f-122">**OFF**</span></span>|  
  
 <span data-ttu-id="a285f-123">Um administrador pode alterar essas configurações de segurança para dar suporte ou restringir cenários específicos em um determinado computador.</span><span class="sxs-lookup"><span data-stu-id="a285f-123">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="a285f-124">Não há ferramentas para alterar a configuração de sinalizador **BindingRedirects** do padrão; um administrador deve editar manualmente o arquivo de Security.config no computador de um usuário.</span><span class="sxs-lookup"><span data-stu-id="a285f-124">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a285f-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="a285f-125">See also</span></span>

- <span data-ttu-id="a285f-126">[Arquivos de política de editor e execução lado a lado](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a285f-126">[Publisher Policy Files and Side-by-Side Execution](/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="a285f-127">Como: Habilitar e desabilitar o redirecionamento automático de associação</span><span class="sxs-lookup"><span data-stu-id="a285f-127">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="a285f-128">Execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="a285f-128">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
