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
ms.openlocfilehash: 67a680727e824cbe29b9e022e00d661e8694f153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780562"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="4a0c1-102">Método ICorProfilerInfo::GetInprocInspectionInterface</span><span class="sxs-lookup"><span data-stu-id="4a0c1-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="4a0c1-103">Obtém um objeto que pode ser consultado para uma interface "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="4a0c1-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="4a0c1-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a0c1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a0c1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a0c1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4a0c1-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="4a0c1-107">[-out](/cpp/atl/iunknown) objeto que pode ser consultado por um `ICorDebugProcess` interface.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a0c1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a0c1-108">Remarks</span></span>  
 <span data-ttu-id="4a0c1-109">O common language runtime (CLR) API de depuração tem suporte limitado depuração em andamento no .NET Framework versão 1.0.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="4a0c1-110">No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="4a0c1-111">Como resultado de comentários do cliente, no processo de depuração foi removido do .NET Framework versão 2.0 e substituída por um conjunto de funcionalidade que é mais alinhada com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="4a0c1-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a0c1-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a0c1-112">Requirements</span></span>  
 <span data-ttu-id="4a0c1-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a0c1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a0c1-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a0c1-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a0c1-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a0c1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a0c1-116">**Versão do .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="4a0c1-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0c1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a0c1-117">See also</span></span>

- [<span data-ttu-id="4a0c1-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4a0c1-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
