---
title: Permissão de segurança para redirecionamento de associações de assemblies
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b9b9ac5c4e8ce08b9f926b0cdf7149dbdd9ac2da
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388960"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="23421-102">Permissão de segurança para redirecionamento de associações de assemblies</span><span class="sxs-lookup"><span data-stu-id="23421-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="23421-103">O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança.</span><span class="sxs-lookup"><span data-stu-id="23421-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="23421-104">Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="23421-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="23421-105">A permissão é concedida ao definir a <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="23421-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="23421-106">Por padrão, os assemblies gerenciados não têm nenhuma permissão.</span><span class="sxs-lookup"><span data-stu-id="23421-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="23421-107">A permissão de segurança é concedida aos aplicativos executados nas zonas confiáveis (computador local) e zona da Intranet.</span><span class="sxs-lookup"><span data-stu-id="23421-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="23421-108">Aplicativos em execução na zona da Internet estritamente estão proibidos de realizar o redirecionamento de associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="23421-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="23421-109">A permissão não é necessária se o redirecionamento de assembly é executado em um arquivo de política de publicador é controlado pelo editor de componente, ou no arquivo de configuração do computador é controlado pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="23421-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="23421-110">No entanto, a permissão é necessária para um aplicativo ignorar explicitamente a política de publicador usando o [ \<publisherPolicy aplicar = "no" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="23421-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="23421-111">A tabela a seguir mostra o padrão de configurações de segurança para o **BindingRedirects** sinalizador.</span><span class="sxs-lookup"><span data-stu-id="23421-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="23421-112">Zona</span><span class="sxs-lookup"><span data-stu-id="23421-112">Zone</span></span>|<span data-ttu-id="23421-113">Configuração do sinalizador de BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="23421-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="23421-114">Zona confiável (computador local)</span><span class="sxs-lookup"><span data-stu-id="23421-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="23421-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="23421-115">**ON**</span></span>|  
|<span data-ttu-id="23421-116">Zona da intranet</span><span class="sxs-lookup"><span data-stu-id="23421-116">Intranet Zone</span></span>|<span data-ttu-id="23421-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="23421-117">**ON**</span></span>|  
|<span data-ttu-id="23421-118">Zona da Internet</span><span class="sxs-lookup"><span data-stu-id="23421-118">Internet Zone</span></span>|<span data-ttu-id="23421-119">**OFF**</span><span class="sxs-lookup"><span data-stu-id="23421-119">**OFF**</span></span>|  
|<span data-ttu-id="23421-120">Zonas não confiáveis</span><span class="sxs-lookup"><span data-stu-id="23421-120">Untrusted zones</span></span>|<span data-ttu-id="23421-121">**OFF**</span><span class="sxs-lookup"><span data-stu-id="23421-121">**OFF**</span></span>|  
  
 <span data-ttu-id="23421-122">Um administrador pode alterar essas configurações de segurança para oferecer suporte ou restringir os cenários específicos em um determinado computador.</span><span class="sxs-lookup"><span data-stu-id="23421-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="23421-123">Não há nenhuma ferramenta para alterar o **BindingRedirects** sinalizador de configuração do padrão; um administrador deve editar manualmente o arquivo Security config no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="23421-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23421-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23421-124">See Also</span></span>  
 [<span data-ttu-id="23421-125">Arquivos de política de editor e execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="23421-125">Publisher Policy Files and Side-by-Side Execution</span></span>](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="23421-126">Como habilitar e desabilitar o redirecionamento automático de associações</span><span class="sxs-lookup"><span data-stu-id="23421-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="23421-127">Execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="23421-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
