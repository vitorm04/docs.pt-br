---
title: Método ICorProfilerInfo::GetInprocInspectionIThisThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 0a4cb365ca8f7d52be505368a3d769a9728983bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502958"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="c4ae9-102">Método ICorProfilerInfo::GetInprocInspectionIThisThread</span><span class="sxs-lookup"><span data-stu-id="c4ae9-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="c4ae9-103">Obtém um objeto que pode ser consultado para a interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c4ae9-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="c4ae9-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="c4ae9-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ae9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4ae9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4ae9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4ae9-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="c4ae9-107">objeto de [saída](/cpp/atl/iunknown) que pode ser consultado para a `ICorDebugThread` interface.</span><span class="sxs-lookup"><span data-stu-id="c4ae9-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4ae9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4ae9-108">Remarks</span></span>  
 <span data-ttu-id="c4ae9-109">Os serviços de depuração Common Language Runtime (CLR) com suporte para a depuração em processo limitada na versão .NET Framework 1,0.</span><span class="sxs-lookup"><span data-stu-id="c4ae9-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="c4ae9-110">A depuração em processo habilitou um criador de perfil para usar as partes de inspeção da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="c4ae9-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="c4ae9-111">Como resultado dos comentários dos clientes, a depuração em processo foi removida da .NET Framework na versão 2,0 e substituída por um conjunto de funcionalidades que está mais alinhado com a API de criação de perfil.</span><span class="sxs-lookup"><span data-stu-id="c4ae9-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ae9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4ae9-112">Requirements</span></span>  
 <span data-ttu-id="c4ae9-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ae9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ae9-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4ae9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4ae9-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4ae9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4ae9-116">**Versão do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="c4ae9-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ae9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4ae9-117">See also</span></span>

- [<span data-ttu-id="c4ae9-118">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="c4ae9-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
