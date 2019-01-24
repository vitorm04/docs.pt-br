---
title: Método ICLRRuntimeInfo::IsStarted
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb23a8e4237ff9b4b217458150c1f04956e439ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526581"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="dc7d9-102">Método ICLRRuntimeInfo::IsStarted</span><span class="sxs-lookup"><span data-stu-id="dc7d9-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="dc7d9-103">Indica se o tempo de execução foi iniciado (ou seja, se o [método iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) foi chamado e foi concluída com êxito).</span><span class="sxs-lookup"><span data-stu-id="dc7d9-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc7d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc7d9-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc7d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc7d9-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="dc7d9-106">[out] `true` se esse tempo de execução for iniciado; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="dc7d9-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="dc7d9-107">[out] Retorna os sinalizadores que foram usados para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dc7d9-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc7d9-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="dc7d9-108">Return Value</span></span>  
 <span data-ttu-id="dc7d9-109">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="dc7d9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dc7d9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc7d9-110">HRESULT</span></span>|<span data-ttu-id="dc7d9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc7d9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc7d9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc7d9-112">S_OK</span></span>|<span data-ttu-id="dc7d9-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="dc7d9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="dc7d9-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="dc7d9-114">E_NOTIMPL</span></span>|<span data-ttu-id="dc7d9-115">A versão do common language runtime (CLR) é anterior à versão do CLR no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc7d9-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc7d9-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc7d9-116">Remarks</span></span>  
 <span data-ttu-id="dc7d9-117">Esse método não funciona com versões do CLR anterior à versão do CLR no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc7d9-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc7d9-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc7d9-118">Requirements</span></span>  
 <span data-ttu-id="dc7d9-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc7d9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc7d9-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="dc7d9-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dc7d9-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dc7d9-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc7d9-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc7d9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc7d9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc7d9-123">See also</span></span>
- [<span data-ttu-id="dc7d9-124">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="dc7d9-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="dc7d9-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="dc7d9-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="dc7d9-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="dc7d9-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
