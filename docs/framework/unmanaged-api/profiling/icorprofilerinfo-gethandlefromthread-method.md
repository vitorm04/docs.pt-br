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
ms.openlocfilehash: 9658ad8a1963d3747fb7c23dce84790a30b17db3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453216"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="5bd96-102">Método ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="5bd96-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="5bd96-103">A ID de um thread é mapeado para um identificador de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="5bd96-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bd96-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bd96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5bd96-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5bd96-106">[in] A ID do thread a ser mapeada.</span><span class="sxs-lookup"><span data-stu-id="5bd96-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="5bd96-107">[out] Um ponteiro para um identificador de thread Win32.</span><span class="sxs-lookup"><span data-stu-id="5bd96-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bd96-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bd96-108">Remarks</span></span>  
 <span data-ttu-id="5bd96-109">O criador de perfil deve chamar o Win32 `DuplicateHandle` função no identificador do antes de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5bd96-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd96-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5bd96-110">Requirements</span></span>  
 <span data-ttu-id="5bd96-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bd96-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd96-112">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5bd96-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5bd96-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bd96-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bd96-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd96-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd96-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bd96-115">See Also</span></span>  
 [<span data-ttu-id="5bd96-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5bd96-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
