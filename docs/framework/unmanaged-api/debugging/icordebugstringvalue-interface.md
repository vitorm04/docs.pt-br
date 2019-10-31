---
title: Interface ICorDebugStringValue
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: d1d3a5eb6e0b24b40a35c13a99465dd3c7032a91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138950"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="2da05-102">Interface ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="2da05-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="2da05-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2da05-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2da05-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2da05-104">Methods</span></span>  
  
|<span data-ttu-id="2da05-105">Método</span><span class="sxs-lookup"><span data-stu-id="2da05-105">Method</span></span>|<span data-ttu-id="2da05-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2da05-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2da05-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="2da05-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="2da05-108">Obtém o número de caracteres na cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="2da05-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="2da05-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="2da05-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="2da05-110">Obtém a cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="2da05-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2da05-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2da05-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2da05-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="2da05-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2da05-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2da05-113">Requirements</span></span>  
 <span data-ttu-id="2da05-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2da05-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2da05-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2da05-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2da05-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2da05-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2da05-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2da05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2da05-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2da05-118">See also</span></span>

- [<span data-ttu-id="2da05-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2da05-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
