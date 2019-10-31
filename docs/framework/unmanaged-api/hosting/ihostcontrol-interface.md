---
title: Interface IHostControl
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195877"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="86981-102">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="86981-102">IHostControl Interface</span></span>
<span data-ttu-id="86981-103">Fornece métodos para configurar o carregamento de assemblies e para determinar a quais interfaces de hospedagem o host dá suporte.</span><span class="sxs-lookup"><span data-stu-id="86981-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86981-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="86981-104">Methods</span></span>  
  
|<span data-ttu-id="86981-105">Método</span><span class="sxs-lookup"><span data-stu-id="86981-105">Method</span></span>|<span data-ttu-id="86981-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="86981-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86981-107">Método GetHostManager</span><span class="sxs-lookup"><span data-stu-id="86981-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="86981-108">Obtém um ponteiro de interface para a implementação do host da interface com o `IID`especificado.</span><span class="sxs-lookup"><span data-stu-id="86981-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="86981-109">Método SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="86981-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="86981-110">Notifica o host de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="86981-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86981-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86981-111">Requirements</span></span>  
 <span data-ttu-id="86981-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86981-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86981-113">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86981-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86981-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86981-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86981-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86981-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86981-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86981-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="86981-117">Interface ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="86981-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="86981-118">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="86981-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="86981-119">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="86981-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
