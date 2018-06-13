---
title: Método ICorProfilerInfo::GetCurrentThreadID
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89f7ff2c213dc510268f9e6c802813a48e870d99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453839"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="b726b-102">Método ICorProfilerInfo::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="b726b-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="b726b-103">Obtém a ID do thread atual, caso se trate de um thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b726b-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b726b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b726b-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b726b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b726b-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="b726b-106">[out] Um ponteiro para o ID retornado do thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b726b-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b726b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b726b-107">Remarks</span></span>  
 <span data-ttu-id="b726b-108">Se o segmento atual é um thread de tempo de execução interno ou outro thread não gerenciado, `GetCurrentThreadID` retorna CORPROF_E_NOT_MANAGED_THREAD como o HRESULT e o valor retornado do `pThreadId` parâmetro será nulo.</span><span class="sxs-lookup"><span data-stu-id="b726b-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b726b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b726b-109">Requirements</span></span>  
 <span data-ttu-id="b726b-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b726b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b726b-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b726b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b726b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b726b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b726b-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b726b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b726b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b726b-114">See Also</span></span>  
 [<span data-ttu-id="b726b-115">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b726b-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
