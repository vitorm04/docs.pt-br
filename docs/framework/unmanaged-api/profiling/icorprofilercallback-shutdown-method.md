---
title: Método ICorProfilerCallback::Shutdown
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: f6873de1a864489d144a671b1a9e1349eaf77d15
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503170"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="438ae-102">Método ICorProfilerCallback::Shutdown</span><span class="sxs-lookup"><span data-stu-id="438ae-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="438ae-103">Notifica o criador de perfil de que o aplicativo está sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="438ae-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="438ae-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="438ae-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="438ae-105">Remarks</span></span>  
 <span data-ttu-id="438ae-106">O código do criador de perfil não pode chamar com segurança os métodos da interface [ICorProfilerInfo](icorprofilerinfo-interface.md) depois que o `Shutdown` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="438ae-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="438ae-107">Todas as chamadas para `ICorProfilerInfo` métodos resultam em um comportamento indefinido após o `Shutdown` método retornar.</span><span class="sxs-lookup"><span data-stu-id="438ae-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="438ae-108">Determinados eventos imutáveis ainda podem ocorrer após o desligamento; o criador de perfil deve tomar cuidado para retornar imediatamente quando isso ocorrer.</span><span class="sxs-lookup"><span data-stu-id="438ae-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="438ae-109">O `Shutdown` método será chamado somente se o aplicativo gerenciado que está sendo criado para o perfil for iniciado como código gerenciado (ou seja, o quadro inicial na pilha de processo é gerenciado).</span><span class="sxs-lookup"><span data-stu-id="438ae-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="438ae-110">Se o aplicativo foi iniciado como código não gerenciado, mas posteriormente entrou em código gerenciado, criando uma instância do Common Language Runtime (CLR) e, em seguida, `Shutdown` não será chamado.</span><span class="sxs-lookup"><span data-stu-id="438ae-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="438ae-111">Nesses casos, o criador de perfil deve incluir em sua biblioteca uma `DllMain` rotina que usa o valor DLL_PROCESS_DETACH para liberar todos os recursos e executar o processamento de limpeza de seus dados, como a liberação de rastreamentos para o disco e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="438ae-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="438ae-112">Em geral, o criador de perfil deve lidar com desligamentos inesperados.</span><span class="sxs-lookup"><span data-stu-id="438ae-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="438ae-113">Por exemplo, um processo pode ser interrompido pelo método Win32's `TerminateProcess` (declarado em Winbase. h).</span><span class="sxs-lookup"><span data-stu-id="438ae-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="438ae-114">Em outros casos, o CLR irá parar determinados threads gerenciados (threads em segundo plano) sem fornecer mensagens de destruição ordenada para eles.</span><span class="sxs-lookup"><span data-stu-id="438ae-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="438ae-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="438ae-115">Requirements</span></span>  
 <span data-ttu-id="438ae-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="438ae-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="438ae-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="438ae-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="438ae-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="438ae-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="438ae-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="438ae-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438ae-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="438ae-120">See also</span></span>

- [<span data-ttu-id="438ae-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="438ae-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="438ae-122">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="438ae-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)
