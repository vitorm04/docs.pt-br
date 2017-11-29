---
title: "Permissão de segurança para redirecionamento de associações de assemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ddaf9965a3b3b5d6171a643b198db93309afad48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="322a3-102">Permissão de segurança para redirecionamento de associações de assemblies</span><span class="sxs-lookup"><span data-stu-id="322a3-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="322a3-103">O redirecionamento de associação de assembly explícito em um arquivo de configuração do aplicativo requer uma permissão de segurança.</span><span class="sxs-lookup"><span data-stu-id="322a3-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="322a3-104">Isso se aplica ao redirecionamento de assemblies do .NET Framework e assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="322a3-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="322a3-105">A permissão é concedida, definindo o <xref:System.Security.Permissions.SecurityPermissionFlag> sinalizador no <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="322a3-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="322a3-106">Assemblies gerenciados não têm permissões por padrão.</span><span class="sxs-lookup"><span data-stu-id="322a3-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="322a3-107">É concedida a permissão de segurança para aplicativos em execução nas zonas confiáveis (computador local) e zona da Intranet.</span><span class="sxs-lookup"><span data-stu-id="322a3-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="322a3-108">Aplicativos em execução na zona da Internet são estritamente proibidos de realizar o redirecionamento de associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="322a3-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="322a3-109">A permissão não é necessária se o redirecionamento de assembly é executado em um arquivo de política de editor é controlado pelo editor de componente, ou no arquivo de configuração da máquina é controlado pelo administrador.</span><span class="sxs-lookup"><span data-stu-id="322a3-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="322a3-110">No entanto, a permissão é necessária para um aplicativo ignorar explicitamente a política de publicador usando o [ \<publisherPolicy aplicar = "no" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="322a3-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="322a3-111">A tabela a seguir mostra o padrão de configurações de segurança para o **BindingRedirects** sinalizador.</span><span class="sxs-lookup"><span data-stu-id="322a3-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="322a3-112">Zona</span><span class="sxs-lookup"><span data-stu-id="322a3-112">Zone</span></span>|<span data-ttu-id="322a3-113">Configuração do sinalizador de BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="322a3-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="322a3-114">Zona confiável (computador local)</span><span class="sxs-lookup"><span data-stu-id="322a3-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="322a3-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="322a3-115">**ON**</span></span>|  
|<span data-ttu-id="322a3-116">Zona de intranet</span><span class="sxs-lookup"><span data-stu-id="322a3-116">Intranet Zone</span></span>|<span data-ttu-id="322a3-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="322a3-117">**ON**</span></span>|  
|<span data-ttu-id="322a3-118">Zona da Internet</span><span class="sxs-lookup"><span data-stu-id="322a3-118">Internet Zone</span></span>|<span data-ttu-id="322a3-119">**DESATIVAR**</span><span class="sxs-lookup"><span data-stu-id="322a3-119">**OFF**</span></span>|  
|<span data-ttu-id="322a3-120">Zonas não confiáveis</span><span class="sxs-lookup"><span data-stu-id="322a3-120">Untrusted zones</span></span>|<span data-ttu-id="322a3-121">**DESATIVAR**</span><span class="sxs-lookup"><span data-stu-id="322a3-121">**OFF**</span></span>|  
  
 <span data-ttu-id="322a3-122">Um administrador pode alterar essas configurações de segurança para oferecer suporte ou restringir cenários específicos em um determinado computador.</span><span class="sxs-lookup"><span data-stu-id="322a3-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="322a3-123">Não há ferramentas para alterar o **BindingRedirects** sinalizador definindo o padrão; um administrador deve editar manualmente o arquivo Security config no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="322a3-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322a3-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="322a3-124">See Also</span></span>  
 [<span data-ttu-id="322a3-125">Arquivos de política do publicador e execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="322a3-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="322a3-126">Como habilitar e desabilitar o redirecionamento automático de associações</span><span class="sxs-lookup"><span data-stu-id="322a3-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="322a3-127">Execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="322a3-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
