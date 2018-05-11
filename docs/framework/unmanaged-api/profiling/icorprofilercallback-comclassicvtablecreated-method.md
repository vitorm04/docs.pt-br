---
title: Método ICorProfilerCallback::COMClassicVTableCreated
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2dcb45fcc987952ec5e84cc468dda8d8ede38bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="1c6f7-102">Método ICorProfilerCallback::COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="1c6f7-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="1c6f7-103">Notifica o criador de perfil que foi criada uma vtable interoperabilidade COM para o IID e a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c6f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c6f7-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c6f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c6f7-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="1c6f7-106">[in] A ID da classe para a qual o vtable foi criado.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="1c6f7-107">[in] A ID da interface implementada pela classe.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="1c6f7-108">Esse valor pode ser NULL se a interface é somente interna.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="1c6f7-109">[in] Um ponteiro para o início de vtable.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="1c6f7-110">[in] O número de slots que estão em de vtable.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c6f7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c6f7-111">Remarks</span></span>  
 <span data-ttu-id="1c6f7-112">O criador de perfil não deve bloquear em sua implementação deste método porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1c6f7-113">Se o criador de perfil bloqueia aqui e uma tentativa de coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1c6f7-114">A implementação do criador de perfil do método não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="1c6f7-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c6f7-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c6f7-115">Requirements</span></span>  
 <span data-ttu-id="1c6f7-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c6f7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c6f7-117">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c6f7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c6f7-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c6f7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c6f7-119">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c6f7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6f7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c6f7-120">See Also</span></span>  
 [<span data-ttu-id="1c6f7-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="1c6f7-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1c6f7-122">Método COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="1c6f7-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
