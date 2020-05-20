---
title: Interface IAppDomainSetup
ms.date: 03/30/2017
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
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617055"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="aceac-102">Interface IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="aceac-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="aceac-103">Fornece propriedades que permitem ao host configurar um <xref:System.AppDomain?displayProperty=nameWithType> tipo antes de chamar o método [ICorRuntimeHost:: CreateDomainEx](icorruntimehost-createdomainex-method.md) para criá-lo.</span><span class="sxs-lookup"><span data-stu-id="aceac-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aceac-104">Propriedades</span><span class="sxs-lookup"><span data-stu-id="aceac-104">Properties</span></span>  
  
|<span data-ttu-id="aceac-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="aceac-105">Property</span></span>|<span data-ttu-id="aceac-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="aceac-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="aceac-107">Obtém ou define o nome do diretório que contém o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aceac-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="aceac-108">Obtém ou define o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aceac-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="aceac-109">Obtém ou define o nome de uma área específica para o aplicativo em que os arquivos são copiados por sombra.</span><span class="sxs-lookup"><span data-stu-id="aceac-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="aceac-110">Obtém ou define o nome do arquivo de configuração para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aceac-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="aceac-111">Obtém ou define o nome do diretório onde os arquivos gerados dinamicamente são armazenados e acessados.</span><span class="sxs-lookup"><span data-stu-id="aceac-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="aceac-112">Obtém ou define o caminho para o arquivo de licença que está associado a esse domínio.</span><span class="sxs-lookup"><span data-stu-id="aceac-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="aceac-113">Obtém ou define a lista de diretórios combinados com o <xref:System.AppDomainSetup.ApplicationBase%2A> diretório para investigação de assemblies privados.</span><span class="sxs-lookup"><span data-stu-id="aceac-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="aceac-114">Obtém ou define um valor de cadeia de caracteres que inclui ou exclui <xref:System.AppDomainSetup.ApplicationBase%2A> do caminho de pesquisa para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aceac-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="aceac-115">Obtém ou define os nomes dos diretórios que contêm assemblies a serem copiados por sombra.</span><span class="sxs-lookup"><span data-stu-id="aceac-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="aceac-116">Obtém ou define uma cadeia de caracteres que indica se a cópia de sombra está ativada ou desativada.</span><span class="sxs-lookup"><span data-stu-id="aceac-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="aceac-117">Os valores válidos são "true" ou "false".</span><span class="sxs-lookup"><span data-stu-id="aceac-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aceac-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="aceac-118">Remarks</span></span>  
 <span data-ttu-id="aceac-119">A `IAppDomainSetup` interface corresponde à interface gerenciada <xref:System.IAppDomainSetup> , que o <xref:System.AppDomainSetup> tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="aceac-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="aceac-120">Consulte <xref:System.IAppDomainSetup?displayProperty=nameWithType> para obter descrições detalhadas de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="aceac-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="aceac-121">`IAppDomainSetup`representa informações de associação de assembly que podem ser adicionadas a uma <xref:System.AppDomain> instância antes da sua criação.</span><span class="sxs-lookup"><span data-stu-id="aceac-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="aceac-122">Por exemplo, um host pode definir a <xref:System.AppDomainSetup.ApplicationBase%2A> propriedade para estabelecer um diretório raiz, que o Common Language Runtime (CLR) testa para assemblies gerenciados.</span><span class="sxs-lookup"><span data-stu-id="aceac-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aceac-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aceac-123">Requirements</span></span>  
 <span data-ttu-id="aceac-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aceac-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aceac-125">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aceac-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aceac-126">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aceac-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aceac-127">**.NET Framework versões:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aceac-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aceac-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="aceac-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="aceac-129">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="aceac-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
