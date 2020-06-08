---
title: Método ICorProfilerInfo::GetThreadInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 532288364b2db1e6be49b9e6f87019b1e41e6866
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497914"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="567d3-102">Método ICorProfilerInfo::GetThreadInfo</span><span class="sxs-lookup"><span data-stu-id="567d3-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="567d3-103">Obtém a identidade do Thread Win32 atual para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="567d3-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="567d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="567d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="567d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="567d3-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="567d3-106">no A ID do thread para o qual obter a ID do Win32 atual.</span><span class="sxs-lookup"><span data-stu-id="567d3-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="567d3-107">fora Um ponteiro para a ID de thread do Win32 atual do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="567d3-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="567d3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="567d3-108">Requirements</span></span>  
 <span data-ttu-id="567d3-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="567d3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="567d3-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="567d3-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="567d3-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="567d3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="567d3-112">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="567d3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="567d3-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="567d3-113">See also</span></span>

- [<span data-ttu-id="567d3-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="567d3-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
