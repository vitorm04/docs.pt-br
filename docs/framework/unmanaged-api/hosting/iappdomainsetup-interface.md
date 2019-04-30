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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970021"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="f6478-102">Interface IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="f6478-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="f6478-103">Fornece propriedades que permitem que o host configurar uma <xref:System.AppDomain?displayProperty=nameWithType> tipo antes de chamar o [icorruntimehost:: Createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) método para criá-lo.</span><span class="sxs-lookup"><span data-stu-id="f6478-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f6478-104">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f6478-104">Properties</span></span>  
  
|<span data-ttu-id="f6478-105">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f6478-105">Property</span></span>|<span data-ttu-id="f6478-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6478-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="f6478-107">Obtém ou define o nome do diretório que contém o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6478-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="f6478-108">Obtém ou define o nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6478-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="f6478-109">Obtém ou define o nome de uma área específica para o aplicativo em que arquivos são copiados em sombra.</span><span class="sxs-lookup"><span data-stu-id="f6478-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="f6478-110">Obtém ou define o nome do arquivo de configuração para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6478-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="f6478-111">Obtém ou define o nome do diretório onde os arquivos gerados dinamicamente são armazenados e acessados.</span><span class="sxs-lookup"><span data-stu-id="f6478-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="f6478-112">Obtém ou define o caminho para o arquivo de licença que está associado esse domínio.</span><span class="sxs-lookup"><span data-stu-id="f6478-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="f6478-113">Obtém ou define a lista de diretórios, combinado com o <xref:System.AppDomainSetup.ApplicationBase%2A> diretório para investigar assemblies particulares.</span><span class="sxs-lookup"><span data-stu-id="f6478-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="f6478-114">Obtém ou define um valor de cadeia de caracteres que inclui ou exclui <xref:System.AppDomainSetup.ApplicationBase%2A> do caminho de pesquisa para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6478-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="f6478-115">Obtém ou define os nomes dos diretórios que contêm assemblies a serem copiados em sombra.</span><span class="sxs-lookup"><span data-stu-id="f6478-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="f6478-116">Obtém ou define uma cadeia de caracteres que indica se a cópia de sombra é ativada ou desativada.</span><span class="sxs-lookup"><span data-stu-id="f6478-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="f6478-117">Valores válidos são "true" ou "false".</span><span class="sxs-lookup"><span data-stu-id="f6478-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6478-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6478-118">Remarks</span></span>  
 <span data-ttu-id="f6478-119">O `IAppDomainSetup` interface corresponde à gerenciado <xref:System.IAppDomainSetup> interface, que o <xref:System.AppDomainSetup> tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="f6478-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="f6478-120">Consulte <xref:System.IAppDomainSetup?displayProperty=nameWithType> para obter descrições detalhadas de suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="f6478-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="f6478-121">`IAppDomainSetup` representa as informações de associação de assembly que podem ser adicionadas a um <xref:System.AppDomain> instância antes de sua criação.</span><span class="sxs-lookup"><span data-stu-id="f6478-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="f6478-122">Por exemplo, um host pode definir o <xref:System.AppDomainSetup.ApplicationBase%2A> assemblies gerenciados de propriedade para estabelecer um diretório raiz, que investiga o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f6478-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6478-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6478-123">Requirements</span></span>  
 <span data-ttu-id="f6478-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6478-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6478-125">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6478-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6478-126">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f6478-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6478-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6478-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6478-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6478-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="f6478-129">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f6478-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
