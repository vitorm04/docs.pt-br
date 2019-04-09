---
title: Método ICLRRuntimeInfo::BindAsLegacyV2Runtime
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 647c87b6f42b01922a385d502d72410af3140cd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095341"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="137a9-102">Método ICLRRuntimeInfo::BindAsLegacyV2Runtime</span><span class="sxs-lookup"><span data-stu-id="137a9-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="137a9-103">Associa o tempo de execução atual para todos os herdados common language runtime (CLR) versão 2 ativação decisões de política.</span><span class="sxs-lookup"><span data-stu-id="137a9-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="137a9-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="137a9-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="137a9-105">Return Value</span></span>  
 <span data-ttu-id="137a9-106">Esse método retorna os HRESULTs específicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="137a9-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="137a9-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="137a9-107">HRESULT</span></span>|<span data-ttu-id="137a9-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="137a9-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="137a9-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="137a9-109">S_OK</span></span>|<span data-ttu-id="137a9-110">Ou a associação foi bem-sucedida ou esse tempo de execução já foram associado como execução de política 2 de ativação de versão herdado CLR.</span><span class="sxs-lookup"><span data-stu-id="137a9-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="137a9-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="137a9-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="137a9-112">Um tempo de execução diferente já foi associado à política de 2 de ativação de versão do CLR herdada.</span><span class="sxs-lookup"><span data-stu-id="137a9-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="137a9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="137a9-113">Remarks</span></span>  
 <span data-ttu-id="137a9-114">Se o tempo de execução atual já está associado para todos os herdados CLR versão 2 ativação política decisões (por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo o [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) no arquivo de configuração), esse método não retorna um resultado de erro; em vez disso, o resultado é S_OK, assim como seria se o método tinha associada com êxito a política de ativação herdados.</span><span class="sxs-lookup"><span data-stu-id="137a9-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137a9-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="137a9-115">Requirements</span></span>  
 <span data-ttu-id="137a9-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137a9-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="137a9-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="137a9-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="137a9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="137a9-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="137a9-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="137a9-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="137a9-120">See also</span></span>

- [<span data-ttu-id="137a9-121">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="137a9-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="137a9-122">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="137a9-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="137a9-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="137a9-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="137a9-124">\<inicialização > elemento</span><span class="sxs-lookup"><span data-stu-id="137a9-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
