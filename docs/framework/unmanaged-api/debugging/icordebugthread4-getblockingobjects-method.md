---
title: "Método ICorDebugThread4::GetBlockingObjects"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6783d7f9af67acdff147cc46ea4f856f9b10bf3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="4c2e6-102">Método ICorDebugThread4::GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="4c2e6-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="4c2e6-103">Fornece uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas que fornecem informações de bloqueio de thread.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c2e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c2e6-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c2e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c2e6-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="4c2e6-106">[out] Um ponteiro para uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c2e6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c2e6-107">Remarks</span></span>  
 <span data-ttu-id="4c2e6-108">O primeiro elemento na enumeração retornado corresponde à estrutura primeiro que está bloqueando o thread.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="4c2e6-109">O segundo elemento corresponde a um item de bloqueio que é encontrado durante a execução de uma procedimento assíncrona chamada quando bloqueado no primeiro e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="4c2e6-110">A enumeração é válida apenas para a duração do atual estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="4c2e6-111">Esse método deve ser chamado enquanto o depurador está em um estado sincronizado.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="4c2e6-112">Se `ppBlockingObjectEnum` não é um ponteiro válido, o resultado é indefinido.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="4c2e6-113">Se um thread está bloqueado e o erro não pode ser determinado, o método retorna um HRESULT que indica falha; Caso contrário, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="4c2e6-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c2e6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c2e6-114">Requirements</span></span>  
 <span data-ttu-id="4c2e6-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c2e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c2e6-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c2e6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c2e6-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c2e6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c2e6-118">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c2e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2e6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c2e6-119">See Also</span></span>  
 [<span data-ttu-id="4c2e6-120">Interface ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="4c2e6-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="4c2e6-121">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="4c2e6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4c2e6-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="4c2e6-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
