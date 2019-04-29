---
title: Método ICorProfilerInfo2::GetThreadAppDomain
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a69f948b936dd80ab364583dc2928778b34ba0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791567"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="b0e05-102">Método ICorProfilerInfo2::GetThreadAppDomain</span><span class="sxs-lookup"><span data-stu-id="b0e05-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="b0e05-103">Obtém a ID do domínio do aplicativo no qual o thread especificado está executando código.</span><span class="sxs-lookup"><span data-stu-id="b0e05-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0e05-104">Syntax</span></span>  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0e05-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0e05-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b0e05-106">[in] A ID especificando o thread.</span><span class="sxs-lookup"><span data-stu-id="b0e05-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="b0e05-107">[out] Um ponteiro para a ID do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0e05-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e05-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0e05-108">Requirements</span></span>  
 <span data-ttu-id="b0e05-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e05-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e05-110">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0e05-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0e05-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0e05-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0e05-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e05-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e05-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0e05-113">See also</span></span>

- [<span data-ttu-id="b0e05-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b0e05-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b0e05-115">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="b0e05-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
