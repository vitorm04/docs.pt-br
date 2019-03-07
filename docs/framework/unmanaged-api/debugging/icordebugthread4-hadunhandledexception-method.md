---
title: Método ICorDebugThread4::HadUnhandledException
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ef4049ee8b1a4881128047b4d7e50fd0a28ea31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499193"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="43813-102">Método ICorDebugThread4::HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="43813-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="43813-103">Indica se o thread nunca teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="43813-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43813-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43813-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="43813-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43813-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="43813-106">[out] Um ponteiro para o endereço de uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="43813-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43813-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43813-107">Return Value</span></span>  
 <span data-ttu-id="43813-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="43813-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="43813-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43813-109">HRESULT</span></span>|<span data-ttu-id="43813-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="43813-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43813-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="43813-111">S_OK</span></span>|<span data-ttu-id="43813-112">O thread teve uma exceção sem tratamento desde sua criação.</span><span class="sxs-lookup"><span data-stu-id="43813-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="43813-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="43813-113">S_FALSE</span></span>|<span data-ttu-id="43813-114">O thread nunca teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="43813-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43813-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="43813-115">Remarks</span></span>  
 <span data-ttu-id="43813-116">Este método indica se o thread nunca teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="43813-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="43813-117">No momento, o retorno de chamada de exceção sem tratamento é acionado ou nativo de anexação JIT é iniciada, esse método é garantido para retornar S_OK.</span><span class="sxs-lookup"><span data-stu-id="43813-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="43813-118">Não há nenhuma garantia de que o [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) método retornará a exceção sem tratamento; no entanto, ele se o processo não ainda foi continuado depois de obter o retorno de chamada de exceção sem tratamento ou após nativo de anexação JIT.</span><span class="sxs-lookup"><span data-stu-id="43813-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="43813-119">Além disso, é possível (embora improvável) ter mais de um thread com uma exceção sem tratamento ao tempo nativo de anexação JIT é disparado.</span><span class="sxs-lookup"><span data-stu-id="43813-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="43813-120">Nesse caso, não há nenhuma maneira de determinar qual exceção disparou a anexação JIT.</span><span class="sxs-lookup"><span data-stu-id="43813-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43813-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43813-121">Requirements</span></span>  
 <span data-ttu-id="43813-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43813-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43813-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43813-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43813-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43813-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43813-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43813-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43813-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43813-126">See also</span></span>
- [<span data-ttu-id="43813-127">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="43813-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="43813-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="43813-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="43813-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="43813-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
