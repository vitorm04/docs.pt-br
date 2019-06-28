---
title: Método ICorProfilerCallback::COMClassicVTableDestroyed
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ace1ecaebe076be3576304ce0a3cc72e119c96d2
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421891"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="3a224-102">Método ICorProfilerCallback::COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="3a224-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="3a224-103">Notifica o criador de perfil que está sendo destruída uma vtable interoperabilidade do COM.</span><span class="sxs-lookup"><span data-stu-id="3a224-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a224-104">Esse retorno de chamada é provavelmente nunca ocorrer, pois a destruição de vtables ocorre muito perto de desligamento.</span><span class="sxs-lookup"><span data-stu-id="3a224-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a224-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a224-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a224-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a224-106">Parameters</span></span>  
 `wrappedClassId`  
 <span data-ttu-id="3a224-107">[in] A ID da classe para o qual este vtable foi criado.</span><span class="sxs-lookup"><span data-stu-id="3a224-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="3a224-108">[in] A ID da interface implementada pela classe.</span><span class="sxs-lookup"><span data-stu-id="3a224-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="3a224-109">Esse valor pode ser NULL se a interface é somente interna.</span><span class="sxs-lookup"><span data-stu-id="3a224-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="3a224-110">[in] Um ponteiro para o início do vtable.</span><span class="sxs-lookup"><span data-stu-id="3a224-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a224-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a224-111">Remarks</span></span>  
 <span data-ttu-id="3a224-112">O criador de perfil não deve bloquear em sua implementação desse método, porque a pilha não pode estar em um estado que permite a coleta de lixo e, portanto, a coleta de lixo preemptive não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="3a224-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3a224-113">Se o criador de perfil bloqueia aqui e coleta de lixo é tentada, o tempo de execução será bloqueada até que esse retorno de chamada retorne.</span><span class="sxs-lookup"><span data-stu-id="3a224-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3a224-114">Implementação do criador de perfil deste método não deve chamar código gerenciado ou em qualquer forma de causa uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="3a224-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a224-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a224-115">Requirements</span></span>  
 <span data-ttu-id="3a224-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a224-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a224-117">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a224-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a224-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a224-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a224-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a224-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a224-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a224-120">See also</span></span>

- [<span data-ttu-id="3a224-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="3a224-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="3a224-122">Método COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="3a224-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
