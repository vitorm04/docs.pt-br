---
title: Método ICorProfilerCallback::ModuleAttachedToAssembly
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: cb342b1c328daca5b3cfc0440e6f276ae54e3ed8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866176"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="59df1-102">Método ICorProfilerCallback::ModuleAttachedToAssembly</span><span class="sxs-lookup"><span data-stu-id="59df1-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="59df1-103">Notifica o criador de perfil de que um módulo está sendo anexado a seu assembly pai.</span><span class="sxs-lookup"><span data-stu-id="59df1-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59df1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59df1-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59df1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59df1-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="59df1-106">no A ID do módulo que está sendo anexado.</span><span class="sxs-lookup"><span data-stu-id="59df1-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="59df1-107">no A ID do assembly pai ao qual o módulo está anexado.</span><span class="sxs-lookup"><span data-stu-id="59df1-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59df1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="59df1-108">Remarks</span></span>  
 <span data-ttu-id="59df1-109">Um módulo pode ser carregado por meio de uma tabela de endereços de importação (IAT), por meio de uma chamada para `LoadLibrary`ou por meio de uma referência de metadados.</span><span class="sxs-lookup"><span data-stu-id="59df1-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="59df1-110">Como resultado, o carregador de Common Language Runtime (CLR) tem vários caminhos de código para determinar o assembly no qual um módulo reside.</span><span class="sxs-lookup"><span data-stu-id="59df1-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="59df1-111">Portanto, é possível que, após [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) seja chamado, o módulo não saiba em qual assembly ele está e obter a ID do assembly pai não é possível.</span><span class="sxs-lookup"><span data-stu-id="59df1-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="59df1-112">O método `ModuleAttachedToAssembly` é chamado quando o módulo é anexado a seu assembly pai e sua ID de assembly pai pode ser obtida.</span><span class="sxs-lookup"><span data-stu-id="59df1-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59df1-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="59df1-113">Requirements</span></span>  
 <span data-ttu-id="59df1-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59df1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59df1-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="59df1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59df1-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59df1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59df1-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59df1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59df1-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="59df1-118">See also</span></span>

- [<span data-ttu-id="59df1-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="59df1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
