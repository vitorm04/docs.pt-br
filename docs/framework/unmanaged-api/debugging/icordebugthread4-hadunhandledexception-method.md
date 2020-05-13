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
ms.openlocfilehash: 4d954057c519263da49f8aaeeeef6ab9402b6956
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378369"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="f1094-102">Método ICorDebugThread4::HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="f1094-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="f1094-103">Indica se o thread já teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="f1094-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1094-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1094-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1094-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1094-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="f1094-106">fora Um ponteiro para o endereço de uma enumeração ordenada de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f1094-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1094-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f1094-107">Return Value</span></span>  
 <span data-ttu-id="f1094-108">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="f1094-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f1094-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1094-109">HRESULT</span></span>|<span data-ttu-id="f1094-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1094-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1094-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1094-111">S_OK</span></span>|<span data-ttu-id="f1094-112">O thread teve uma exceção sem tratamento desde sua criação.</span><span class="sxs-lookup"><span data-stu-id="f1094-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="f1094-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f1094-113">S_FALSE</span></span>|<span data-ttu-id="f1094-114">O thread nunca teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="f1094-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1094-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1094-115">Remarks</span></span>  
 <span data-ttu-id="f1094-116">Esse método indica se o thread já teve uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="f1094-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="f1094-117">No momento em que o retorno de chamada de exceção sem tratamento é acionado ou a anexação JIT nativa é iniciada, esse método é garantido para retornar S_OK.</span><span class="sxs-lookup"><span data-stu-id="f1094-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="f1094-118">Não há nenhuma garantia de que o método [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) retornará a exceção sem tratamento; no entanto, ele será se o processo ainda não tiver sido continuado depois de obter o retorno de chamada de exceção sem tratamento ou após a anexação JIT nativa.</span><span class="sxs-lookup"><span data-stu-id="f1094-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="f1094-119">Além disso, é possível (embora improvável) ter mais de um thread com uma exceção sem tratamento no momento em que a anexação JIT nativa é disparada.</span><span class="sxs-lookup"><span data-stu-id="f1094-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="f1094-120">Nesse caso, não há como determinar qual exceção disparou a anexação JIT.</span><span class="sxs-lookup"><span data-stu-id="f1094-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1094-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1094-121">Requirements</span></span>  
 <span data-ttu-id="f1094-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1094-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1094-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1094-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1094-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1094-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1094-125">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1094-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1094-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1094-126">See also</span></span>

- [<span data-ttu-id="f1094-127">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="f1094-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="f1094-128">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f1094-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f1094-129">Depuração</span><span class="sxs-lookup"><span data-stu-id="f1094-129">Debugging</span></span>](index.md)
