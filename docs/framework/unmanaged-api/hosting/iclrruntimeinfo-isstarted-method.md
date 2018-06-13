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
ms.openlocfilehash: 8934a2a51ea4bc86166bf99a6087124d03ab11d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434110"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="a8a89-102">Método ICLRRuntimeInfo::IsStarted</span><span class="sxs-lookup"><span data-stu-id="a8a89-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="a8a89-103">Indica se o tempo de execução foi iniciado (ou seja, se o [método Iclrruntimehost::](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) foi chamado e teve êxito).</span><span class="sxs-lookup"><span data-stu-id="a8a89-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8a89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8a89-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8a89-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8a89-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="a8a89-106">[out] `true` se esse tempo de execução for iniciada; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a8a89-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="a8a89-107">[out] Retorna os sinalizadores que foram usados para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a8a89-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8a89-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a8a89-108">Return Value</span></span>  
 <span data-ttu-id="a8a89-109">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="a8a89-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a8a89-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8a89-110">HRESULT</span></span>|<span data-ttu-id="a8a89-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8a89-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8a89-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8a89-112">S_OK</span></span>|<span data-ttu-id="a8a89-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a8a89-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a8a89-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a8a89-114">E_NOTIMPL</span></span>|<span data-ttu-id="a8a89-115">A versão de runtime (CLR) de linguagem comum é anterior à versão do CLR no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8a89-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8a89-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8a89-116">Remarks</span></span>  
 <span data-ttu-id="a8a89-117">Esse método funciona com CLR versões anteriores à versão de CLR no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8a89-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8a89-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8a89-118">Requirements</span></span>  
 <span data-ttu-id="a8a89-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8a89-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8a89-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a8a89-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a8a89-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a8a89-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8a89-122">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8a89-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a89-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8a89-123">See Also</span></span>  
 [<span data-ttu-id="a8a89-124">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a8a89-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="a8a89-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="a8a89-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a8a89-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a8a89-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
