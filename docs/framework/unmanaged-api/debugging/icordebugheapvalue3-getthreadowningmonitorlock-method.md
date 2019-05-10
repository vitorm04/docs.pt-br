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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a713a7d1f6e6a9d4b22071c33ac8e7c38cd371b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665088"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="a786b-102">Método ICorDebugHeapValue3::GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="a786b-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="a786b-103">Retorna o thread gerenciado que detém o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="a786b-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a786b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a786b-104">Syntax</span></span>  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a786b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a786b-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="a786b-106">[out] O thread gerenciado que detém o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="a786b-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="a786b-107">[out] O número de vezes que esse thread terá de liberar o bloqueio antes de retornar ao que está sendo sem proprietário.</span><span class="sxs-lookup"><span data-stu-id="a786b-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a786b-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a786b-108">Return Value</span></span>  
 <span data-ttu-id="a786b-109">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="a786b-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a786b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a786b-110">HRESULT</span></span>|<span data-ttu-id="a786b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a786b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a786b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a786b-112">S_OK</span></span>|<span data-ttu-id="a786b-113">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a786b-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a786b-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a786b-114">S_FALSE</span></span>|<span data-ttu-id="a786b-115">Nenhum thread gerenciado detém o bloqueio de monitor nesse objeto.</span><span class="sxs-lookup"><span data-stu-id="a786b-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a786b-116">Exceções</span><span class="sxs-lookup"><span data-stu-id="a786b-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a786b-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a786b-117">Remarks</span></span>  
 <span data-ttu-id="a786b-118">Se um thread gerenciado detém o bloqueio de monitor nesse objeto:</span><span class="sxs-lookup"><span data-stu-id="a786b-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="a786b-119">O método retorna S_OK.</span><span class="sxs-lookup"><span data-stu-id="a786b-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="a786b-120">O objeto de thread é válido até que o thread seja encerrado.</span><span class="sxs-lookup"><span data-stu-id="a786b-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="a786b-121">Se nenhum thread gerenciado detém o bloqueio de monitor nesse objeto `ppThread` e `pAcquisitionCount` forem alterados, e o método retorna S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="a786b-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="a786b-122">Se `ppThread` ou `pAcquisitionCount` não for um ponteiro válido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="a786b-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="a786b-123">Se ocorrer um erro, de modo que ele não pode ser determinado que, se houver, o thread possui o bloqueio de monitor nesse objeto, o método retorna um HRESULT que indica falha.</span><span class="sxs-lookup"><span data-stu-id="a786b-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a786b-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a786b-124">Requirements</span></span>  
 <span data-ttu-id="a786b-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a786b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a786b-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a786b-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a786b-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a786b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a786b-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a786b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a786b-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a786b-129">See also</span></span>

- [<span data-ttu-id="a786b-130">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a786b-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a786b-131">Depuração</span><span class="sxs-lookup"><span data-stu-id="a786b-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
