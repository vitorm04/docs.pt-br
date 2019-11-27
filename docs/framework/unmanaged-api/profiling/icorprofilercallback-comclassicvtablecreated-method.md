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
ms.openlocfilehash: 79be2572f52ec509d9551261074204bf62ad5388
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445051"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="af031-102">Método ICorProfilerCallback::COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="af031-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="af031-103">Notifica o criador de perfil de que uma interoperabilidade COM vtable para o IID e a classe especificados foram criados.</span><span class="sxs-lookup"><span data-stu-id="af031-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af031-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af031-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af031-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af031-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="af031-106">no A ID da classe para a qual a vtable foi criada.</span><span class="sxs-lookup"><span data-stu-id="af031-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="af031-107">no A ID da interface implementada pela classe.</span><span class="sxs-lookup"><span data-stu-id="af031-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="af031-108">Esse valor pode ser nulo se a interface for somente interno.</span><span class="sxs-lookup"><span data-stu-id="af031-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="af031-109">no Um ponteiro para o início de vtable.</span><span class="sxs-lookup"><span data-stu-id="af031-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="af031-110">no O número de slots que estão no vtable.</span><span class="sxs-lookup"><span data-stu-id="af031-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af031-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="af031-111">Remarks</span></span>  
 <span data-ttu-id="af031-112">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="af031-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="af031-113">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="af031-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="af031-114">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="af031-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af031-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af031-115">Requirements</span></span>  
 <span data-ttu-id="af031-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af031-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af031-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="af031-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af031-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af031-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af031-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af031-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af031-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af031-120">See also</span></span>

- [<span data-ttu-id="af031-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="af031-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="af031-122">Método COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="af031-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
