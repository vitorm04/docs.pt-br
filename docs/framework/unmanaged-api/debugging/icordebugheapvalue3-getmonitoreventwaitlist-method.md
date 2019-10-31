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
ms.openlocfilehash: 0fbff178efd4d0dff3593907b3d40e946be2ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121303"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="6d418-102">Método ICorDebugHeapValue3::GetMonitorEventWaitList</span><span class="sxs-lookup"><span data-stu-id="6d418-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="6d418-103">Fornece uma lista ordenada de threads que são enfileirados no evento que está associado a um bloqueio de monitor.</span><span class="sxs-lookup"><span data-stu-id="6d418-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d418-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d418-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d418-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d418-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="6d418-106">fora O enumerador ICorDebugThreadEnum que fornece a lista ordenada de threads.</span><span class="sxs-lookup"><span data-stu-id="6d418-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d418-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6d418-107">Return Value</span></span>  
 <span data-ttu-id="6d418-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="6d418-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6d418-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d418-109">HRESULT</span></span>|<span data-ttu-id="6d418-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d418-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d418-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d418-111">S_OK</span></span>|<span data-ttu-id="6d418-112">A lista não está vazia.</span><span class="sxs-lookup"><span data-stu-id="6d418-112">The list is not empty.</span></span>|  
|<span data-ttu-id="6d418-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6d418-113">S_FALSE</span></span>|<span data-ttu-id="6d418-114">A lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="6d418-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6d418-115">Exceções</span><span class="sxs-lookup"><span data-stu-id="6d418-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d418-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d418-116">Remarks</span></span>  
 <span data-ttu-id="6d418-117">O primeiro thread na lista é o primeiro thread que é liberado pela próxima chamada para <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d418-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d418-118">O próximo thread na lista é liberado na chamada a seguir e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="6d418-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="6d418-119">Se a lista não estiver vazia, esse método retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="6d418-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="6d418-120">Se a lista estiver vazia, o método retornará S_FALSE; Nesse caso, a enumeração ainda é válida, embora esteja vazia.</span><span class="sxs-lookup"><span data-stu-id="6d418-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="6d418-121">Em ambos os casos, a interface de enumeração é utilizável somente pela duração do estado atual sincronizado.</span><span class="sxs-lookup"><span data-stu-id="6d418-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="6d418-122">No entanto, as interfaces do thread dispensadas a partir dela são válidas até que o thread saia.</span><span class="sxs-lookup"><span data-stu-id="6d418-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="6d418-123">Se `ppThreadEnum` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="6d418-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="6d418-124">Se ocorrer um erro de modo que não possa ser determinado que, se houver, os threads estão aguardando o monitor, o método retornará um HRESULT que indica falha.</span><span class="sxs-lookup"><span data-stu-id="6d418-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d418-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d418-125">Requirements</span></span>  
 <span data-ttu-id="6d418-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d418-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d418-127">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d418-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d418-128">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d418-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d418-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d418-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d418-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d418-130">See also</span></span>

- [<span data-ttu-id="6d418-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6d418-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6d418-132">Depuração</span><span class="sxs-lookup"><span data-stu-id="6d418-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
