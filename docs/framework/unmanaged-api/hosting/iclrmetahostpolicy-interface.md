---
title: Interface ICLRMetaHostPolicy
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="993ed-102">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="993ed-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="993ed-103">Fornece o [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método, que retorna um ponteiro para uma interface comum de runtime (CLR) de idioma com base em critérios de uma política, gerenciados arquivo de assembly, versão e configuração.</span><span class="sxs-lookup"><span data-stu-id="993ed-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="993ed-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="993ed-104">Methods</span></span>  
  
|<span data-ttu-id="993ed-105">Método</span><span class="sxs-lookup"><span data-stu-id="993ed-105">Method</span></span>|<span data-ttu-id="993ed-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="993ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="993ed-107">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="993ed-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="993ed-108">Fornece uma interface preferencial do CLR com base em critérios de uma política, gerenciados do arquivo de assembly, versão e a configuração.</span><span class="sxs-lookup"><span data-stu-id="993ed-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="993ed-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="993ed-109">Remarks</span></span>  
 <span data-ttu-id="993ed-110">Você pode obter uma referência a esta interface chamando o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funcionar conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="993ed-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="993ed-111">Esta interface, na verdade, não carregar ou ativar o CLR, mas simplesmente retorna a versão do CLR preferencial com base nas versões disponíveis que estão instaladas ou carregadas.</span><span class="sxs-lookup"><span data-stu-id="993ed-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="993ed-112">O [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API de hospedagem consolida políticas para que hosts com necessidades específicas podem usar a funcionalidade básica sem incorrer em penalidades não intencionais.</span><span class="sxs-lookup"><span data-stu-id="993ed-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="993ed-113">Por exemplo, muitos as exportações mscoree associará a um CLR específico, embora um método não logicamente precisará-lo.</span><span class="sxs-lookup"><span data-stu-id="993ed-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="993ed-114">O [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeração fornece diretivas de associação que são comuns para a maioria dos hosts.</span><span class="sxs-lookup"><span data-stu-id="993ed-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="993ed-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="993ed-115">Requirements</span></span>  
 <span data-ttu-id="993ed-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="993ed-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="993ed-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="993ed-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="993ed-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="993ed-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="993ed-119">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="993ed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993ed-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="993ed-120">See Also</span></span>  
 [<span data-ttu-id="993ed-121">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="993ed-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="993ed-122">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="993ed-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="993ed-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="993ed-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
