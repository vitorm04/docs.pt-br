---
title: Método ICorDebugHeapValue3::GetMonitorEventWaitList
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27815cf8cb7fdcd1c01f26391c317d52bbb388ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628507"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="17993-102">Método ICorDebugHeapValue3::GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="17993-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="17993-103">Fornece uma lista ordenada de threads que estão na fila o evento que está associado com um bloqueio do monitor.</span><span class="sxs-lookup"><span data-stu-id="17993-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17993-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17993-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17993-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17993-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="17993-106">[out] O enumerador ICorDebugThreadEnum que fornece a lista ordenada de threads.</span><span class="sxs-lookup"><span data-stu-id="17993-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17993-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="17993-107">Return Value</span></span>  
 <span data-ttu-id="17993-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="17993-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="17993-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17993-109">HRESULT</span></span>|<span data-ttu-id="17993-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="17993-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17993-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="17993-111">S_OK</span></span>|<span data-ttu-id="17993-112">A lista não está vazia.</span><span class="sxs-lookup"><span data-stu-id="17993-112">The list is not empty.</span></span>|  
|<span data-ttu-id="17993-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="17993-113">S_FALSE</span></span>|<span data-ttu-id="17993-114">A lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="17993-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="17993-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="17993-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17993-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="17993-116">Remarks</span></span>  
 <span data-ttu-id="17993-117">O primeiro thread na lista é o primeiro thread que é lançado pela próxima chamada para <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="17993-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17993-118">O próximo thread na lista é liberado na chamada a seguir e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="17993-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="17993-119">Se a lista não estiver vazia, esse método retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="17993-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="17993-120">Se a lista estiver vazia, o método retorna S_FALSE; Nesse caso, a enumeração é ainda é válida, embora ele está vazio.</span><span class="sxs-lookup"><span data-stu-id="17993-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="17993-121">Em ambos os casos, a interface de enumeração é utilizável apenas para a duração do estado atual de sincronizado.</span><span class="sxs-lookup"><span data-stu-id="17993-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="17993-122">No entanto, as interfaces do thread liberadas dele são válidos até que o thread seja encerrado.</span><span class="sxs-lookup"><span data-stu-id="17993-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="17993-123">Se `ppThreadEnum` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="17993-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="17993-124">Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, segmentos estão aguardando o monitor, o método retorna um HRESULT que indica falha.</span><span class="sxs-lookup"><span data-stu-id="17993-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17993-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17993-125">Requirements</span></span>  
 <span data-ttu-id="17993-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17993-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17993-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17993-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17993-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17993-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17993-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17993-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17993-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17993-130">See also</span></span>
- [<span data-ttu-id="17993-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="17993-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="17993-132">Depuração</span><span class="sxs-lookup"><span data-stu-id="17993-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
