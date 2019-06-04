---
title: Interface ICLRMetaHostPolicy
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426d77114d3deeff94c39e2f5fc1f2e56e753641
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490282"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="3df31-102">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="3df31-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="3df31-103">Fornece o [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) gerenciados de método, que retorna um ponteiro para uma interface de runtime (CLR) de linguagem comum com base em um critério de política, arquivo de assembly, versão e configuração.</span><span class="sxs-lookup"><span data-stu-id="3df31-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3df31-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3df31-104">Methods</span></span>  
  
|<span data-ttu-id="3df31-105">Método</span><span class="sxs-lookup"><span data-stu-id="3df31-105">Method</span></span>|<span data-ttu-id="3df31-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3df31-107">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="3df31-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="3df31-108">Fornece uma interface preferencial do CLR com base em um critério de política, gerenciados do arquivo de assembly, versão e configuração.</span><span class="sxs-lookup"><span data-stu-id="3df31-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3df31-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3df31-109">Remarks</span></span>  
 <span data-ttu-id="3df31-110">Você pode obter uma referência a esta interface por meio da chamada a [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funcionar conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3df31-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="3df31-111">Essa interface, na verdade não carregar ou ativar o CLR, mas retorna apenas a versão do CLR preferencial com base nas versões disponíveis que estão instaladas ou carregadas.</span><span class="sxs-lookup"><span data-stu-id="3df31-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="3df31-112">A API de hospedagem do .NET Framework 4 consolida as políticas para que hosts com necessidades específicas podem usar a funcionalidade básica sem incorrer em multas não intencionais.</span><span class="sxs-lookup"><span data-stu-id="3df31-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="3df31-113">Por exemplo, muitas das exportações mscoree. dll serão associado a um CLR específico, embora um método pode exigi-lo logicamente.</span><span class="sxs-lookup"><span data-stu-id="3df31-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="3df31-114">O [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeração fornece políticas de associação que são comuns à maioria dos hosts.</span><span class="sxs-lookup"><span data-stu-id="3df31-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df31-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3df31-115">Requirements</span></span>  
 <span data-ttu-id="3df31-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df31-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df31-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3df31-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3df31-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3df31-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3df31-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df31-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df31-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3df31-120">See also</span></span>

- [<span data-ttu-id="3df31-121">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="3df31-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="3df31-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="3df31-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="3df31-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="3df31-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
