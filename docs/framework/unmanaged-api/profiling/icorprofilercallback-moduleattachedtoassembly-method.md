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
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503387"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="cb530-102">Método ICorProfilerCallback::ModuleAttachedToAssembly</span><span class="sxs-lookup"><span data-stu-id="cb530-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="cb530-103">Notifica o criador de perfil de que um módulo está sendo anexado a seu assembly pai.</span><span class="sxs-lookup"><span data-stu-id="cb530-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb530-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb530-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb530-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb530-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="cb530-106">no A ID do módulo que está sendo anexado.</span><span class="sxs-lookup"><span data-stu-id="cb530-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="cb530-107">no A ID do assembly pai ao qual o módulo está anexado.</span><span class="sxs-lookup"><span data-stu-id="cb530-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb530-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb530-108">Remarks</span></span>  
 <span data-ttu-id="cb530-109">Um módulo pode ser carregado por meio de uma tabela de endereços de importação (IAT), por meio de uma chamada para `LoadLibrary` ou por meio de uma referência de metadados.</span><span class="sxs-lookup"><span data-stu-id="cb530-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="cb530-110">Como resultado, o carregador de Common Language Runtime (CLR) tem vários caminhos de código para determinar o assembly no qual um módulo reside.</span><span class="sxs-lookup"><span data-stu-id="cb530-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="cb530-111">Portanto, é possível que, após [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) seja chamado, o módulo não saiba em qual assembly ele está e obter a ID do assembly pai não é possível.</span><span class="sxs-lookup"><span data-stu-id="cb530-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="cb530-112">O `ModuleAttachedToAssembly` método é chamado quando o módulo é anexado a seu assembly pai e sua ID de assembly pai pode ser obtida.</span><span class="sxs-lookup"><span data-stu-id="cb530-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb530-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb530-113">Requirements</span></span>  
 <span data-ttu-id="cb530-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb530-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb530-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb530-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb530-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb530-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb530-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb530-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb530-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb530-118">See also</span></span>

- [<span data-ttu-id="cb530-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="cb530-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
