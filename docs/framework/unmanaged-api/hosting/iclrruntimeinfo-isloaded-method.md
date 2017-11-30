---
title: "Método ICLRRuntimeInfo::IsLoaded"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoaded
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac7ed77dd4cb141257a1b73ccd433c7d17ee1f38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="d06c5-102">Método ICLRRuntimeInfo::IsLoaded</span><span class="sxs-lookup"><span data-stu-id="d06c5-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="d06c5-103">Indica se o common language runtime (CLR) associado com o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface é carregada em um processo.</span><span class="sxs-lookup"><span data-stu-id="d06c5-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="d06c5-104">Um tempo de execução pode ser carregado sem também ter sido iniciada.</span><span class="sxs-lookup"><span data-stu-id="d06c5-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06c5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d06c5-105">Syntax</span></span>  
  
```  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d06c5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d06c5-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="d06c5-107">[in] Um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="d06c5-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="d06c5-108">[out] `true` se o CLR é carregado no processo; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="d06c5-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d06c5-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d06c5-109">Return Value</span></span>  
 <span data-ttu-id="d06c5-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="d06c5-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d06c5-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d06c5-111">HRESULT</span></span>|<span data-ttu-id="d06c5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d06c5-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d06c5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d06c5-113">S_OK</span></span>|<span data-ttu-id="d06c5-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d06c5-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d06c5-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d06c5-115">E_POINTER</span></span>|<span data-ttu-id="d06c5-116">`pbLoaded` é nulo.</span><span class="sxs-lookup"><span data-stu-id="d06c5-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d06c5-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d06c5-117">Remarks</span></span>  
 <span data-ttu-id="d06c5-118">Esse método é compatível com as seguintes funções e interfaces:</span><span class="sxs-lookup"><span data-stu-id="d06c5-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
-   <span data-ttu-id="d06c5-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (no .NET Framework versão 1 API de hospedagem).</span><span class="sxs-lookup"><span data-stu-id="d06c5-119">[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
-   <span data-ttu-id="d06c5-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (no .NET Framework 2.0 API de hospedagem).</span><span class="sxs-lookup"><span data-stu-id="d06c5-120">[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
-   <span data-ttu-id="d06c5-121">Preterido `CorBindTo*` funções (consulte [funções de hospedagem de CLR preterido](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) na API de hospedagem do .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="d06c5-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="d06c5-122">Um host pode chamar uma das `CorBindTo*` funções, como o [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) função, para criar uma instância de uma versão específica do CLR.</span><span class="sxs-lookup"><span data-stu-id="d06c5-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="d06c5-123">O host pode então chamar o [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) método e especifique o mesmo número de versão para obter um [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="d06c5-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="d06c5-124">Se o host, em seguida, chama o `IsLoaded` método retornado [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` retorna `true`; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="d06c5-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d06c5-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d06c5-125">Requirements</span></span>  
 <span data-ttu-id="d06c5-126">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d06c5-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d06c5-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d06c5-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d06c5-128">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d06c5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d06c5-129">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d06c5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06c5-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d06c5-130">See Also</span></span>  
 [<span data-ttu-id="d06c5-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="d06c5-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="d06c5-132">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d06c5-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d06c5-133">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="d06c5-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
