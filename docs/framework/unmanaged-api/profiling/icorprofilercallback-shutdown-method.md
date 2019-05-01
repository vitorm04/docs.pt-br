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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041747"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="653da-102">Método ICorProfilerCallback::Shutdown</span><span class="sxs-lookup"><span data-stu-id="653da-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="653da-103">Notifica o criador de perfil que o aplicativo está sendo desligado.</span><span class="sxs-lookup"><span data-stu-id="653da-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="653da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="653da-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="653da-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="653da-105">Remarks</span></span>  
 <span data-ttu-id="653da-106">O código do criador de perfil com segurança não é possível chamar métodos do [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface após o `Shutdown` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="653da-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="653da-107">Todas as chamadas para `ICorProfilerInfo` métodos resultam em comportamento indefinido após a `Shutdown` retorno do método.</span><span class="sxs-lookup"><span data-stu-id="653da-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="653da-108">Determinados eventos imutáveis ainda poderão ocorrer após o desligamento; o criador de perfil deve cuidar para retornar imediatamente quando isso ocorre.</span><span class="sxs-lookup"><span data-stu-id="653da-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="653da-109">O `Shutdown` método será chamado apenas se o aplicativo gerenciado que está sendo analisado começou como código gerenciado (ou seja, o quadro inicial na pilha de processo é gerenciado).</span><span class="sxs-lookup"><span data-stu-id="653da-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="653da-110">Se o aplicativo de início do código não gerenciado, mas posteriormente entrou no código gerenciado, criando uma instância do common language runtime (CLR), em seguida, `Shutdown` não será chamado.</span><span class="sxs-lookup"><span data-stu-id="653da-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="653da-111">Nesses casos, o criador de perfil deve incluir em sua biblioteca de um `DllMain` rotina que usa o DLL_PROCESS_DETACH valor para liberar todos os recursos e executar o processamento de limpar seus dados, como liberar os rastreamentos no disco e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="653da-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="653da-112">Em geral, o criador de perfil deve lidar com desligamentos inesperados.</span><span class="sxs-lookup"><span data-stu-id="653da-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="653da-113">Por exemplo, um processo pode ser interrompido por do Win32 `TerminateProcess` método (declarado em Winbase).</span><span class="sxs-lookup"><span data-stu-id="653da-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="653da-114">Em outros casos, o CLR interromperá a determinados threads gerenciados (threads de segundo plano) sem a entrega de mensagens de destruição ordenada para eles.</span><span class="sxs-lookup"><span data-stu-id="653da-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="653da-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="653da-115">Requirements</span></span>  
 <span data-ttu-id="653da-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="653da-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="653da-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="653da-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="653da-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="653da-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="653da-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="653da-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653da-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="653da-120">See also</span></span>

- [<span data-ttu-id="653da-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="653da-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="653da-122">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="653da-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
