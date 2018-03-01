---
title: Interface IAppDomainSetup
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9db1b787015231b3d9053d4ed316cb70c5db96ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="cdf74-102">Interface IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="cdf74-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="cdf74-103">Fornece propriedades que permitem que o host configurar um <xref:System.AppDomain?displayProperty=nameWithType> tipo antes de chamar o [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método criá-la.</span><span class="sxs-lookup"><span data-stu-id="cdf74-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cdf74-104">Propriedades</span><span class="sxs-lookup"><span data-stu-id="cdf74-104">Properties</span></span>  
  
|<span data-ttu-id="cdf74-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="cdf74-105">Property</span></span>|<span data-ttu-id="cdf74-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdf74-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="cdf74-107">Obtém ou define o nome do diretório que contém o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdf74-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="cdf74-108">Obtém ou define o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdf74-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="cdf74-109">Obtém ou define o nome de uma área específica para o aplicativo em arquivos são copiados de sombra.</span><span class="sxs-lookup"><span data-stu-id="cdf74-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="cdf74-110">Obtém ou define o nome do arquivo de configuração para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdf74-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="cdf74-111">Obtém ou define o nome do diretório onde os arquivos gerados dinamicamente são armazenados e acessados.</span><span class="sxs-lookup"><span data-stu-id="cdf74-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="cdf74-112">Obtém ou define o caminho para o arquivo de licença que está associado este domínio.</span><span class="sxs-lookup"><span data-stu-id="cdf74-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="cdf74-113">Obtém ou define a lista de pastas, combinada com a <xref:System.AppDomainSetup.ApplicationBase%2A> diretório para investigação de assemblies privados.</span><span class="sxs-lookup"><span data-stu-id="cdf74-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="cdf74-114">Obtém ou define um valor de cadeia de caracteres que inclua ou exclua <xref:System.AppDomainSetup.ApplicationBase%2A> do caminho de pesquisa para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdf74-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="cdf74-115">Obtém ou define os nomes dos diretórios que contêm assemblies para ser copiado de sombra.</span><span class="sxs-lookup"><span data-stu-id="cdf74-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="cdf74-116">Obtém ou define uma cadeia de caracteres que indica se a cópia de sombra é ativada ou desativada.</span><span class="sxs-lookup"><span data-stu-id="cdf74-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="cdf74-117">Os valores válidos são "verdadeiro" ou "false".</span><span class="sxs-lookup"><span data-stu-id="cdf74-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf74-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdf74-118">Remarks</span></span>  
 <span data-ttu-id="cdf74-119">O `IAppDomainSetup` interface corresponde à gerenciado <xref:System.IAppDomainSetup> interface, que o <xref:System.AppDomainSetup> tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="cdf74-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="cdf74-120">Consulte <xref:System.IAppDomainSetup?displayProperty=nameWithType> para obter descrições detalhadas de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="cdf74-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="cdf74-121">`IAppDomainSetup`representa as informações de associação de assembly que podem ser adicionadas a um <xref:System.AppDomain> instância antes de sua criação.</span><span class="sxs-lookup"><span data-stu-id="cdf74-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="cdf74-122">Por exemplo, um host pode definir o <xref:System.AppDomainSetup.ApplicationBase%2A> gerenciados de propriedade para estabelecer um diretório raiz que o common language runtime (CLR) sondas para assemblies.</span><span class="sxs-lookup"><span data-stu-id="cdf74-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf74-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdf74-123">Requirements</span></span>  
 <span data-ttu-id="cdf74-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdf74-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdf74-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cdf74-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cdf74-126">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cdf74-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdf74-127">**Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdf74-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf74-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdf74-128">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [<span data-ttu-id="cdf74-129">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="cdf74-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
