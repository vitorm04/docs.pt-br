---
title: Método ICorDebugHeapValue3::GetThreadOwningMonitorLock
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: 9cc68e39dfef096b8ab6a8ba743f7a516cc349be
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210404"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="690a1-102">Método ICorDebugHeapValue3::GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="690a1-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="690a1-103">Retorna o thread gerenciado que possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="690a1-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="690a1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="690a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="690a1-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="690a1-106">fora O thread gerenciado que possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="690a1-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="690a1-107">fora O número de vezes que esse thread teria que liberar o bloqueio antes que ele retorne sem proprietário.</span><span class="sxs-lookup"><span data-stu-id="690a1-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="690a1-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="690a1-108">Return Value</span></span>  
 <span data-ttu-id="690a1-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="690a1-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="690a1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="690a1-110">HRESULT</span></span>|<span data-ttu-id="690a1-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="690a1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="690a1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="690a1-112">S_OK</span></span>|<span data-ttu-id="690a1-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="690a1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="690a1-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="690a1-114">S_FALSE</span></span>|<span data-ttu-id="690a1-115">Nenhum thread gerenciado possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="690a1-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="690a1-116">Exceções</span><span class="sxs-lookup"><span data-stu-id="690a1-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="690a1-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="690a1-117">Remarks</span></span>  
 <span data-ttu-id="690a1-118">Se um thread gerenciado possuir o bloqueio de monitor neste objeto:</span><span class="sxs-lookup"><span data-stu-id="690a1-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="690a1-119">O método retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="690a1-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="690a1-120">O objeto de thread é válido até que o thread saia.</span><span class="sxs-lookup"><span data-stu-id="690a1-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="690a1-121">Se nenhum thread gerenciado possuir o bloqueio de monitor nesse objeto `ppThread` e não `pAcquisitionCount` for alterado, e o método retornar S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="690a1-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="690a1-122">Se `ppThread` ou `pAcquisitionCount` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="690a1-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="690a1-123">Se ocorrer um erro de modo que não possa ser determinado que, se houver, thread possui o bloqueio de monitor nesse objeto, o método retornará um HRESULT que indica falha.</span><span class="sxs-lookup"><span data-stu-id="690a1-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="690a1-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="690a1-124">Requirements</span></span>  
 <span data-ttu-id="690a1-125">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="690a1-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="690a1-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="690a1-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="690a1-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="690a1-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="690a1-128">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="690a1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690a1-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="690a1-129">See also</span></span>

- [<span data-ttu-id="690a1-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="690a1-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="690a1-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="690a1-131">Debugging</span></span>](index.md)
