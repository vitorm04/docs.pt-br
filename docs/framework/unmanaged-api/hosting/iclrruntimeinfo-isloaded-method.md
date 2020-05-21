---
title: Método ICLRRuntimeInfo::IsLoaded
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762520"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="6011d-102">Método ICLRRuntimeInfo::IsLoaded</span><span class="sxs-lookup"><span data-stu-id="6011d-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="6011d-103">Indica se o Common Language Runtime (CLR) associado à interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) é carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="6011d-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="6011d-104">Um tempo de execução pode ser carregado sem também ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="6011d-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6011d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6011d-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6011d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6011d-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="6011d-107">no Um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="6011d-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="6011d-108">[fora] `true` Se o CLR for carregado no processo; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="6011d-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6011d-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6011d-109">Return Value</span></span>  
 <span data-ttu-id="6011d-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="6011d-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6011d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6011d-111">HRESULT</span></span>|<span data-ttu-id="6011d-112">Description</span><span class="sxs-lookup"><span data-stu-id="6011d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6011d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6011d-113">S_OK</span></span>|<span data-ttu-id="6011d-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="6011d-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6011d-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6011d-115">E_POINTER</span></span>|<span data-ttu-id="6011d-116">`pbLoaded` é nulo.</span><span class="sxs-lookup"><span data-stu-id="6011d-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6011d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="6011d-117">Remarks</span></span>  
 <span data-ttu-id="6011d-118">Esse método é compatível com versões anteriores com as seguintes funções e interfaces:</span><span class="sxs-lookup"><span data-stu-id="6011d-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="6011d-119">Interface [ICorRuntimeHost](icorruntimehost-interface.md) (na API de hospedagem do .NET Framework versão 1).</span><span class="sxs-lookup"><span data-stu-id="6011d-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="6011d-120">Interface [ICLRRuntimeHost](iclrruntimehost-interface.md) (na API de hospedagem .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="6011d-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="6011d-121">Funções preteridas `CorBindTo*` (consulte [funções de Hospedagem de CLR preteridas](deprecated-clr-hosting-functions.md) na API de hospedagem .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="6011d-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="6011d-122">Um host pode chamar uma das funções preteridas `CorBindTo*` , como a função [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , para instanciar uma versão específica do CLR.</span><span class="sxs-lookup"><span data-stu-id="6011d-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="6011d-123">O host poderia então chamar o método [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) e especificar o mesmo número de versão para obter uma interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6011d-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="6011d-124">Se o host chamar o `IsLoaded` método na interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) retornada, `pbLoaded` retornará `true` ; caso contrário, retornará `false` .</span><span class="sxs-lookup"><span data-stu-id="6011d-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6011d-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6011d-125">Requirements</span></span>  
 <span data-ttu-id="6011d-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6011d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6011d-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6011d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6011d-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6011d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6011d-129">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6011d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6011d-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="6011d-130">See also</span></span>

- [<span data-ttu-id="6011d-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="6011d-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6011d-132">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6011d-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6011d-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="6011d-133">Hosting</span></span>](index.md)
