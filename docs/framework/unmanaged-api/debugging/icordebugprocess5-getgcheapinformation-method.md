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
ms.openlocfilehash: 703f159c5bc6b73dcd0e770bdeb61f676aae034c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792372"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="b28f6-102">Método ICorDebugProcess5::GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="b28f6-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="b28f6-103">Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele é enumerável no momento.</span><span class="sxs-lookup"><span data-stu-id="b28f6-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b28f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b28f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b28f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b28f6-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="b28f6-106">fora Um ponteiro para um valor [COR_HEAPINFO](cor-heapinfo-structure.md) que fornece informações gerais sobre o heap de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b28f6-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b28f6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b28f6-107">Remarks</span></span>  
 <span data-ttu-id="b28f6-108">O método de `ICorDebugProcess5::GetGCHeapInformation` deve ser chamado antes de enumerar o heap ou regiões de heap individuais para garantir que as estruturas de coleta de lixo no processo sejam válidas no momento.</span><span class="sxs-lookup"><span data-stu-id="b28f6-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="b28f6-109">O heap de coleta de lixo não pode ser movimentado enquanto uma coleção está em andamento.</span><span class="sxs-lookup"><span data-stu-id="b28f6-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="b28f6-110">Caso contrário, a enumeração poderá capturar as estruturas de coleta de lixo que são inválidas.</span><span class="sxs-lookup"><span data-stu-id="b28f6-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b28f6-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b28f6-111">Requirements</span></span>  
 <span data-ttu-id="b28f6-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b28f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b28f6-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b28f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b28f6-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b28f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b28f6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b28f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28f6-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="b28f6-116">See also</span></span>

- [<span data-ttu-id="b28f6-117">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="b28f6-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="b28f6-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b28f6-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
