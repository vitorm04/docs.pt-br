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
ms.openlocfilehash: ec265525d01dab0669939569501fce91b500a900
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127500"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="96f07-102">Método ICorDebugHeapValue3::GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="96f07-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="96f07-103">Retorna o thread gerenciado que possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="96f07-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96f07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96f07-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="96f07-106">fora O thread gerenciado que possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="96f07-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="96f07-107">fora O número de vezes que esse thread teria que liberar o bloqueio antes que ele retorne sem proprietário.</span><span class="sxs-lookup"><span data-stu-id="96f07-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96f07-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="96f07-108">Return Value</span></span>  
 <span data-ttu-id="96f07-109">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="96f07-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="96f07-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96f07-110">HRESULT</span></span>|<span data-ttu-id="96f07-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="96f07-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96f07-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="96f07-112">S_OK</span></span>|<span data-ttu-id="96f07-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="96f07-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="96f07-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="96f07-114">S_FALSE</span></span>|<span data-ttu-id="96f07-115">Nenhum thread gerenciado possui o bloqueio de monitor neste objeto.</span><span class="sxs-lookup"><span data-stu-id="96f07-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="96f07-116">Exceções</span><span class="sxs-lookup"><span data-stu-id="96f07-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f07-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="96f07-117">Remarks</span></span>  
 <span data-ttu-id="96f07-118">Se um thread gerenciado possuir o bloqueio de monitor neste objeto:</span><span class="sxs-lookup"><span data-stu-id="96f07-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="96f07-119">O método retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="96f07-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="96f07-120">O objeto de thread é válido até que o thread saia.</span><span class="sxs-lookup"><span data-stu-id="96f07-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="96f07-121">Se nenhum thread gerenciado possuir o bloqueio de monitor nesse objeto, `ppThread` e `pAcquisitionCount` não serão alterados e o método retornará S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="96f07-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="96f07-122">Se `ppThread` ou `pAcquisitionCount` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="96f07-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="96f07-123">Se ocorrer um erro de modo que não possa ser determinado que, se houver, thread possui o bloqueio de monitor nesse objeto, o método retornará um HRESULT que indica falha.</span><span class="sxs-lookup"><span data-stu-id="96f07-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f07-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96f07-124">Requirements</span></span>  
 <span data-ttu-id="96f07-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96f07-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f07-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96f07-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96f07-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96f07-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96f07-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f07-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f07-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96f07-129">See also</span></span>

- [<span data-ttu-id="96f07-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="96f07-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="96f07-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="96f07-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
