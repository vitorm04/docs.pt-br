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
ms.openlocfilehash: 708981155589d491a3b1819adb611a28072dd1bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500307"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="5c858-102">Método ICorProfilerCallback::COMClassicVTableDestroyed</span><span class="sxs-lookup"><span data-stu-id="5c858-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="5c858-103">Notifica o criador de perfil de que uma interoperabilidade COM vtable está sendo destruída.</span><span class="sxs-lookup"><span data-stu-id="5c858-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c858-104">Esse retorno de chamada provavelmente nunca ocorrerá, pois a destruição de vtables ocorre muito perto do desligamento.</span><span class="sxs-lookup"><span data-stu-id="5c858-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c858-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c858-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c858-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5c858-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="5c858-107">\[in] a ID da classe para a qual essa vtable foi criada.</span><span class="sxs-lookup"><span data-stu-id="5c858-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="5c858-108">\[in] a ID da interface implementada pela classe.</span><span class="sxs-lookup"><span data-stu-id="5c858-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="5c858-109">Esse valor pode ser nulo se a interface for somente interno.</span><span class="sxs-lookup"><span data-stu-id="5c858-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="5c858-110">\[in] um ponteiro para o início de vtable.</span><span class="sxs-lookup"><span data-stu-id="5c858-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="5c858-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c858-111">Remarks</span></span>  
 <span data-ttu-id="5c858-112">O criador de perfil não deve bloquear em sua implementação desse método porque a pilha pode não estar em um estado que permita a coleta de lixo e, portanto, a coleta de lixo preemptiva não pode ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="5c858-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="5c858-113">Se o criador de perfil for bloqueado aqui e a coleta de lixo for tentada, o tempo de execução será bloqueado até que esse retorno de chamada seja retornado.</span><span class="sxs-lookup"><span data-stu-id="5c858-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="5c858-114">A implementação do criador de perfil desse método não deve chamar o código gerenciado ou, de qualquer forma, causar uma alocação de memória gerenciada.</span><span class="sxs-lookup"><span data-stu-id="5c858-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c858-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c858-115">Requirements</span></span>  
 <span data-ttu-id="5c858-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c858-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c858-117">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5c858-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c858-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c858-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c858-119">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c858-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c858-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c858-120">See also</span></span>

- [<span data-ttu-id="5c858-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="5c858-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5c858-122">Método COMClassicVTableCreated</span><span class="sxs-lookup"><span data-stu-id="5c858-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
