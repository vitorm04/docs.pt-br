---
title: "Método ICorDebugProcess5::GetGCHeapInformation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetGCHeapInformation
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da423914d8af20c0f942d53ed6ac9f34ace01ca9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="bd897-102">Método ICorDebugProcess5::GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="bd897-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="bd897-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele está atualmente enumerável.</span><span class="sxs-lookup"><span data-stu-id="bd897-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd897-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd897-104">Syntax</span></span>  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd897-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd897-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="bd897-106">[out] Um ponteiro para um [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) valor que fornece informações gerais sobre o heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bd897-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd897-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd897-107">Remarks</span></span>  
 <span data-ttu-id="bd897-108">O `ICorDebugProcess5::GetGCHeapInformation` método deve ser chamado antes de enumerar o heap ou regiões de heap individuais para garantir que a coleta de lixo estruturas no processo são válidos no momento.</span><span class="sxs-lookup"><span data-stu-id="bd897-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="bd897-109">O heap de coleta de lixo não pode ser percorrido durante uma coleção está em andamento.</span><span class="sxs-lookup"><span data-stu-id="bd897-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="bd897-110">Caso contrário, a enumeração pode capturar as estruturas de coleta de lixo que são inválidas.</span><span class="sxs-lookup"><span data-stu-id="bd897-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd897-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd897-111">Requirements</span></span>  
 <span data-ttu-id="bd897-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd897-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd897-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd897-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd897-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd897-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd897-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd897-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd897-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd897-116">See Also</span></span>  
 [<span data-ttu-id="bd897-117">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="bd897-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="bd897-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="bd897-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
