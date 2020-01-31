---
title: Interface ICorDebugValue3
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 5fa042223e47961dad0a6799ab8ca999ef76e285
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791088"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="5390b-102">Interface ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="5390b-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="5390b-103">Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte a matrizes com mais de 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5390b-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5390b-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5390b-104">Methods</span></span>  
  
|<span data-ttu-id="5390b-105">Método</span><span class="sxs-lookup"><span data-stu-id="5390b-105">Method</span></span>|<span data-ttu-id="5390b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5390b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5390b-107">Método GetSize64</span><span class="sxs-lookup"><span data-stu-id="5390b-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="5390b-108">Obtém o tamanho, em bytes, deste `ICorDebugValue3` objeto.</span><span class="sxs-lookup"><span data-stu-id="5390b-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5390b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5390b-109">Remarks</span></span>  
 <span data-ttu-id="5390b-110">O método [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) retorna um tamanho de objeto que varia de 0 a 2.147.483.647 bytes.</span><span class="sxs-lookup"><span data-stu-id="5390b-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="5390b-111">No .NET Framework 4,5, o tamanho das matrizes pode exceder 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5390b-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="5390b-112">A interface `ICorDebugValue3` permite que você determine o tamanho dessas matrizes.</span><span class="sxs-lookup"><span data-stu-id="5390b-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5390b-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5390b-113">Requirements</span></span>  
 <span data-ttu-id="5390b-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5390b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5390b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5390b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5390b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5390b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5390b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5390b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5390b-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="5390b-118">See also</span></span>

- [<span data-ttu-id="5390b-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5390b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5390b-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="5390b-120">Debugging</span></span>](index.md)
