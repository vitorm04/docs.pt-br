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
ms.openlocfilehash: 6c9ec6af90cc47c3c01621563a9813789c25aa1d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500332"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="fb708-102">Método ICorProfilerCallback::COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="fb708-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="fb708-103">Notifica o criador de perfil de que uma interoperabilidade COM vtable para o IID e a classe especificados foram criados.</span><span class="sxs-lookup"><span data-stu-id="fb708-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb708-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb708-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb708-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb708-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="fb708-106">\[in] a ID da classe para a qual a vtable foi criada.</span><span class="sxs-lookup"><span data-stu-id="fb708-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="fb708-107">\[in] a ID da interface implementada pela classe.</span><span class="sxs-lookup"><span data-stu-id="fb708-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="fb708-108">Esse valor pode ser nulo se a interface for somente interno.</span><span class="sxs-lookup"><span data-stu-id="fb708-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="fb708-109">\[in] um ponteiro para o início de vtable.</span><span class="sxs-lookup"><span data-stu-id="fb708-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="fb708-110">\[in] o número de slots que estão no vtable.</span><span class="sxs-lookup"><span data-stu-id="fb708-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb708-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb708-111">Remarks</span></span>  
 <span data-ttu-id="fb708-112">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="fb708-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="fb708-113">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="fb708-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="fb708-114">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="fb708-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb708-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb708-115">Requirements</span></span>  
 <span data-ttu-id="fb708-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb708-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb708-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fb708-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb708-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb708-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb708-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb708-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb708-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb708-120">See also</span></span>

- [<span data-ttu-id="fb708-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="fb708-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fb708-122">Método COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="fb708-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
