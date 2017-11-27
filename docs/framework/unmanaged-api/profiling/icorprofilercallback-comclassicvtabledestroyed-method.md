---
title: "Método ICorProfilerCallback::COMClassicVTableDestroyed"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="a3e8d-102">Método ICorProfilerCallback::COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="a3e8d-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="a3e8d-103">Notifica o criador de perfil que está sendo destruída uma vtable interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3e8d-104">Esse retorno de chamada é provável que nunca ocorrer, porque a destruição do vtables ocorre muito perto de desligamento.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3e8d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3e8d-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3e8d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a3e8d-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="a3e8d-107">[in] A ID da classe para o qual este vtable foi criado.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="a3e8d-108">[in] A ID da interface implementada pela classe.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="a3e8d-109">Esse valor pode ser NULL se a interface é somente interna.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="a3e8d-110">[in] Um ponteiro para o início de vtable.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3e8d-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3e8d-111">Remarks</span></span>  
 <span data-ttu-id="a3e8d-112">O criador de perfil não deve bloquear em sua implementação deste método porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptivo não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="a3e8d-113">Se o criador de perfil bloqueia aqui e uma tentativa de coleta de lixo, tempo de execução será bloqueado até que esse retorno de chamada retorna.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="a3e8d-114">A implementação do criador de perfil do método não deve chamar código gerenciado ou em qualquer causa de maneira uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="a3e8d-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3e8d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3e8d-115">Requirements</span></span>  
 <span data-ttu-id="a3e8d-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3e8d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3e8d-117">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3e8d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3e8d-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3e8d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3e8d-119">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3e8d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e8d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3e8d-120">See Also</span></span>  
 [<span data-ttu-id="a3e8d-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="a3e8d-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a3e8d-122">Método COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="a3e8d-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
