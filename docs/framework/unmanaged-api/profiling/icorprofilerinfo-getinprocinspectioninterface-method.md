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
ms.openlocfilehash: d3fcd859fb11f6a0c660751f16fa175e19e9d03b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439000"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="b9ee3-102">Método ICorProfilerInfo::GetInprocInspectionInterface</span><span class="sxs-lookup"><span data-stu-id="b9ee3-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="b9ee3-103">Obtém um objeto que pode ser consultado para uma interface "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="b9ee3-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="b9ee3-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="b9ee3-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9ee3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9ee3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9ee3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9ee3-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="b9ee3-107">objeto de [saída](/cpp/atl/iunknown) que pode ser consultado para uma interface de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="b9ee3-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9ee3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9ee3-108">Remarks</span></span>  
 <span data-ttu-id="b9ee3-109">A API de depuração Common Language Runtime (CLR) com suporte para a depuração em processo limitada no .NET Framework versão 1,0.</span><span class="sxs-lookup"><span data-stu-id="b9ee3-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="b9ee3-110">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="b9ee3-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="b9ee3-111">Como resultado dos comentários dos clientes, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="b9ee3-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9ee3-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b9ee3-112">Requirements</span></span>  
 <span data-ttu-id="b9ee3-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9ee3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9ee3-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9ee3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9ee3-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9ee3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9ee3-116">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="b9ee3-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9ee3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9ee3-117">See also</span></span>

- [<span data-ttu-id="b9ee3-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b9ee3-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
