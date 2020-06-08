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
ms.openlocfilehash: 45e27ac3c2d4912d2ed3e5d43ea3020b9db5dbdc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504024"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="caaf6-102">Método ICLRRuntimeInfo::IsLoaded</span><span class="sxs-lookup"><span data-stu-id="caaf6-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="caaf6-103">Indica se o Common Language Runtime (CLR) associado à interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) é carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="caaf6-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="caaf6-104">Um tempo de execução pode ser carregado sem também ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="caaf6-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caaf6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="caaf6-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caaf6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="caaf6-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="caaf6-107">no Um identificador para o processo.</span><span class="sxs-lookup"><span data-stu-id="caaf6-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="caaf6-108">[fora] `true` Se o CLR for carregado no processo; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="caaf6-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="caaf6-109">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="caaf6-109">Return Value</span></span>  
 <span data-ttu-id="caaf6-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="caaf6-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="caaf6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="caaf6-111">HRESULT</span></span>|<span data-ttu-id="caaf6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="caaf6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="caaf6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="caaf6-113">S_OK</span></span>|<span data-ttu-id="caaf6-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="caaf6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="caaf6-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="caaf6-115">E_POINTER</span></span>|<span data-ttu-id="caaf6-116">`pbLoaded` é nulo.</span><span class="sxs-lookup"><span data-stu-id="caaf6-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caaf6-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="caaf6-117">Remarks</span></span>  
 <span data-ttu-id="caaf6-118">Esse método é compatível com versões anteriores com as seguintes funções e interfaces:</span><span class="sxs-lookup"><span data-stu-id="caaf6-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="caaf6-119">Interface [ICorRuntimeHost](icorruntimehost-interface.md) (na API de hospedagem do .NET Framework versão 1).</span><span class="sxs-lookup"><span data-stu-id="caaf6-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="caaf6-120">Interface [ICLRRuntimeHost](iclrruntimehost-interface.md) (na API de hospedagem .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="caaf6-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="caaf6-121">Funções preteridas `CorBindTo*` (consulte [funções de Hospedagem de CLR preteridas](deprecated-clr-hosting-functions.md) na API de hospedagem .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="caaf6-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="caaf6-122">Um host pode chamar uma das funções preteridas `CorBindTo*` , como a função [CorBindToRuntime](corbindtoruntime-function.md) , para instanciar uma versão específica do CLR.</span><span class="sxs-lookup"><span data-stu-id="caaf6-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="caaf6-123">O host poderia então chamar o método [ICLRMetaHost:: GetRuntime](iclrmetahost-getruntime-method.md) e especificar o mesmo número de versão para obter uma interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="caaf6-123">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="caaf6-124">Se o host chamar o `IsLoaded` método na interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) retornada, `pbLoaded` retornará `true` ; caso contrário, retornará `false` .</span><span class="sxs-lookup"><span data-stu-id="caaf6-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caaf6-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="caaf6-125">Requirements</span></span>  
 <span data-ttu-id="caaf6-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caaf6-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caaf6-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="caaf6-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="caaf6-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="caaf6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caaf6-129">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caaf6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caaf6-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="caaf6-130">See also</span></span>

- [<span data-ttu-id="caaf6-131">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="caaf6-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="caaf6-132">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="caaf6-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="caaf6-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="caaf6-133">Hosting</span></span>](index.md)
