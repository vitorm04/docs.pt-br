---
title: Método ICorProfilerInfo::GetHandleFromThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f1eb2354536a436bd6ae41cf70bf11549982d5e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612587"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="216c5-102">Método ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="216c5-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="216c5-103">A ID de um thread é mapeado para um identificador de thread do Win32.</span><span class="sxs-lookup"><span data-stu-id="216c5-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="216c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="216c5-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="216c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="216c5-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="216c5-106">[in] A ID do thread a ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="216c5-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="216c5-107">[out] Um ponteiro para um identificador de thread do Win32.</span><span class="sxs-lookup"><span data-stu-id="216c5-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="216c5-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="216c5-108">Remarks</span></span>  
 <span data-ttu-id="216c5-109">O criador de perfil deve chamar o Win32 `DuplicateHandle` função no identificador antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="216c5-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="216c5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="216c5-110">Requirements</span></span>  
 <span data-ttu-id="216c5-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="216c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="216c5-112">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="216c5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="216c5-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="216c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="216c5-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="216c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216c5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="216c5-115">See also</span></span>
- [<span data-ttu-id="216c5-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="216c5-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
