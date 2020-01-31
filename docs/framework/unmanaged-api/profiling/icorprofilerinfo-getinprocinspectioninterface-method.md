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
ms.openlocfilehash: 5c9258126c872bd501b4eebc4698b4dded402dfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863355"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="54b6b-102">Método ICorProfilerInfo::GetInprocInspectionInterface</span><span class="sxs-lookup"><span data-stu-id="54b6b-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="54b6b-103">Obtém um objeto que pode ser consultado para uma interface "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="54b6b-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="54b6b-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="54b6b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b6b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54b6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54b6b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="54b6b-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="54b6b-107">objeto de [saída](/cpp/atl/iunknown) que pode ser consultado para uma interface de `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="54b6b-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54b6b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="54b6b-108">Remarks</span></span>  
 <span data-ttu-id="54b6b-109">A API de depuração Common Language Runtime (CLR) com suporte para a depuração em processo limitada no .NET Framework versão 1,0.</span><span class="sxs-lookup"><span data-stu-id="54b6b-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="54b6b-110">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="54b6b-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="54b6b-111">Como resultado dos comentários dos clientes, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="54b6b-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54b6b-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="54b6b-112">Requirements</span></span>  
 <span data-ttu-id="54b6b-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54b6b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54b6b-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="54b6b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54b6b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54b6b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54b6b-116">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="54b6b-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b6b-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="54b6b-117">See also</span></span>

- [<span data-ttu-id="54b6b-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="54b6b-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
