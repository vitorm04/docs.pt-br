---
title: Método ICorProfilerCallback::AssemblyLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e32af790c755f65b5435455c326d011656da19ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198368"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="80866-102">Método ICorProfilerCallback::AssemblyLoadFinished</span><span class="sxs-lookup"><span data-stu-id="80866-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="80866-103">Notifica o criador de perfil um assembly terminou o carregamento.</span><span class="sxs-lookup"><span data-stu-id="80866-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80866-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80866-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80866-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80866-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="80866-106">[in] Identifica o assembly que foi carregado.</span><span class="sxs-lookup"><span data-stu-id="80866-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="80866-107">[in] Um HRESULT que indica se o assembly de carregamento concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="80866-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80866-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="80866-108">Remarks</span></span>  
 <span data-ttu-id="80866-109">O valor de `assemblyId` não é válido para uma solicitação de informações até que o `AssemblyLoadFinished` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="80866-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="80866-110">Algumas partes de carregar o assembly podem continuar após o `AssemblyLoadFinished` retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="80866-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="80866-111">Uma falha HRESULT em `hrStatus` indica uma falha.</span><span class="sxs-lookup"><span data-stu-id="80866-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="80866-112">No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do carregamento do assembly foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="80866-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80866-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80866-113">Requirements</span></span>  
 <span data-ttu-id="80866-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80866-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80866-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80866-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80866-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80866-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80866-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80866-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80866-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80866-118">See also</span></span>

- [<span data-ttu-id="80866-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="80866-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
