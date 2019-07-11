---
title: Método ICorDebugProcess5::GetGCHeapInformation
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e94034fcdcd8d86f34c61af30a7729a80c913fac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767340"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="565e7-102">Método ICorDebugProcess5::GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="565e7-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="565e7-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele está atualmente enumerável.</span><span class="sxs-lookup"><span data-stu-id="565e7-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="565e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="565e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="565e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="565e7-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="565e7-106">[out] Um ponteiro para um [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) valor que fornece informações gerais sobre o heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="565e7-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="565e7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="565e7-107">Remarks</span></span>  
 <span data-ttu-id="565e7-108">O `ICorDebugProcess5::GetGCHeapInformation` método deve ser chamado antes de enumerar o heap ou regiões de heap individuais para garantir que a coleta de lixo de estruturas no processo serão válidos no momento.</span><span class="sxs-lookup"><span data-stu-id="565e7-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="565e7-109">O heap da coleta de lixo não pode ser percorrido durante uma coleta está em andamento.</span><span class="sxs-lookup"><span data-stu-id="565e7-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="565e7-110">Caso contrário, a enumeração pode capturar as estruturas de coleta de lixo que são inválidas.</span><span class="sxs-lookup"><span data-stu-id="565e7-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="565e7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="565e7-111">Requirements</span></span>  
 <span data-ttu-id="565e7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="565e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="565e7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="565e7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="565e7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="565e7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="565e7-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="565e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565e7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="565e7-116">See also</span></span>

- [<span data-ttu-id="565e7-117">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="565e7-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="565e7-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="565e7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
