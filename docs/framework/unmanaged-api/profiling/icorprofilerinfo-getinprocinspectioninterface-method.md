---
title: Método ICorProfilerInfo::GetInprocInspectionInterface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbb4aa43757df86037d9c883e76ee38cef5eeb86
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494422"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="4a5ca-102">Método ICorProfilerInfo::GetInprocInspectionInterface</span><span class="sxs-lookup"><span data-stu-id="4a5ca-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="4a5ca-103">Obtém um objeto que pode ser consultado para uma interface "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="4a5ca-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="4a5ca-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="4a5ca-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5ca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a5ca-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a5ca-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a5ca-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="4a5ca-107">[-out](/cpp/atl/iunknown) objeto que pode ser consultado por um `ICorDebugProcess` interface.</span><span class="sxs-lookup"><span data-stu-id="4a5ca-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a5ca-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a5ca-108">Remarks</span></span>  
 <span data-ttu-id="4a5ca-109">O common language runtime (CLR) API de depuração tem suporte limitado depuração em andamento no .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="4a5ca-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="4a5ca-110">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="4a5ca-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="4a5ca-111">Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituída por um conjunto de funcionalidade que é mais alinhada com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="4a5ca-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a5ca-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a5ca-112">Requirements</span></span>  
 <span data-ttu-id="4a5ca-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a5ca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a5ca-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a5ca-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a5ca-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a5ca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a5ca-116">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="4a5ca-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5ca-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a5ca-117">See also</span></span>
- [<span data-ttu-id="4a5ca-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4a5ca-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
