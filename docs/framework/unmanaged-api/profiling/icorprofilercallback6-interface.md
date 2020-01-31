---
title: Interface ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864863"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="2adc3-102">Interface ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="2adc3-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="2adc3-103">[Com suporte no .NET Framework 4.5.2 e versões posteriores]</span><span class="sxs-lookup"><span data-stu-id="2adc3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2adc3-104">Uma subclasse de [ICorProfilerCallback5](icorprofilercallback5-interface.md) que fornece um método de retorno de chamada que o Common Language Runtime usa para notificar um criador de perfil que um assembly está carregando.</span><span class="sxs-lookup"><span data-stu-id="2adc3-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2adc3-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2adc3-105">Methods</span></span>  
  
|<span data-ttu-id="2adc3-106">Método</span><span class="sxs-lookup"><span data-stu-id="2adc3-106">Method</span></span>|<span data-ttu-id="2adc3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2adc3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2adc3-108">Método GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="2adc3-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="2adc3-109">Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.</span><span class="sxs-lookup"><span data-stu-id="2adc3-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2adc3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2adc3-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2adc3-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2adc3-111">Requirements</span></span>  
 <span data-ttu-id="2adc3-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2adc3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2adc3-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2adc3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2adc3-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2adc3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2adc3-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="2adc3-115">See also</span></span>

- [<span data-ttu-id="2adc3-116">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="2adc3-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
