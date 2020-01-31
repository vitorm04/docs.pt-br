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
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791345"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="4c00c-102">Método ICorDebugThread4::HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="4c00c-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="4c00c-103">Indica se o thread já teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="4c00c-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c00c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c00c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c00c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c00c-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="4c00c-106">fora Um ponteiro para o endereço de uma enumeração ordenada de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="4c00c-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c00c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4c00c-107">Return Value</span></span>  
 <span data-ttu-id="4c00c-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="4c00c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4c00c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c00c-109">HRESULT</span></span>|<span data-ttu-id="4c00c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c00c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c00c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c00c-111">S_OK</span></span>|<span data-ttu-id="4c00c-112">O thread teve uma exceção sem tratamento desde sua criação.</span><span class="sxs-lookup"><span data-stu-id="4c00c-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="4c00c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4c00c-113">S_FALSE</span></span>|<span data-ttu-id="4c00c-114">O thread nunca teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="4c00c-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c00c-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c00c-115">Remarks</span></span>  
 <span data-ttu-id="4c00c-116">Esse método indica se o thread já teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="4c00c-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="4c00c-117">No momento em que o retorno de chamada de exceção sem tratamento é acionado ou a anexação JIT nativa é iniciada, esse método é garantido para retornar S_OK.</span><span class="sxs-lookup"><span data-stu-id="4c00c-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="4c00c-118">Não há nenhuma garantia de que o método [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) retornará a exceção sem tratamento; no entanto, ele será se o processo ainda não tiver sido continuado depois de obter o retorno de chamada de exceção sem tratamento ou após a anexação JIT nativa.</span><span class="sxs-lookup"><span data-stu-id="4c00c-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="4c00c-119">Além disso, é possível (embora improvável) ter mais de um thread com uma exceção sem tratamento no momento em que a anexação JIT nativa é disparada.</span><span class="sxs-lookup"><span data-stu-id="4c00c-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="4c00c-120">Nesse caso, não há como determinar qual exceção disparou a anexação JIT.</span><span class="sxs-lookup"><span data-stu-id="4c00c-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c00c-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4c00c-121">Requirements</span></span>  
 <span data-ttu-id="4c00c-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c00c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c00c-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c00c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c00c-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c00c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c00c-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c00c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c00c-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c00c-126">See also</span></span>

- [<span data-ttu-id="4c00c-127">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="4c00c-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="4c00c-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4c00c-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4c00c-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="4c00c-129">Debugging</span></span>](index.md)
