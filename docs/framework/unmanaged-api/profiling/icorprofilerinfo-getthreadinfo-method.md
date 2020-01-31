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
ms.openlocfilehash: 7318d7d1494b0cf4db54b92ff09775be5500bdb1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869550"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="707ea-102">Método ICorProfilerInfo::GetThreadInfo</span><span class="sxs-lookup"><span data-stu-id="707ea-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="707ea-103">Obtém a identidade do Thread Win32 atual para o thread especificado.</span><span class="sxs-lookup"><span data-stu-id="707ea-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="707ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="707ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="707ea-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="707ea-106">no A ID do thread para o qual obter a ID do Win32 atual.</span><span class="sxs-lookup"><span data-stu-id="707ea-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="707ea-107">fora Um ponteiro para a ID de thread do Win32 atual do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="707ea-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707ea-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="707ea-108">Requirements</span></span>  
 <span data-ttu-id="707ea-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="707ea-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="707ea-110">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="707ea-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="707ea-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="707ea-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="707ea-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="707ea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707ea-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="707ea-113">See also</span></span>

- [<span data-ttu-id="707ea-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="707ea-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
