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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6709b14ce8e7bc131f9feb7a277fb41851ee4352
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173986"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="11b16-102">Interface ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="11b16-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="11b16-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="11b16-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11b16-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="11b16-104">Methods</span></span>  
  
|<span data-ttu-id="11b16-105">Método</span><span class="sxs-lookup"><span data-stu-id="11b16-105">Method</span></span>|<span data-ttu-id="11b16-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="11b16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11b16-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="11b16-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="11b16-108">Obtém o número de caracteres na cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="11b16-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="11b16-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="11b16-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="11b16-110">Obtém a cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="11b16-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b16-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="11b16-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11b16-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="11b16-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11b16-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11b16-113">Requirements</span></span>  
 <span data-ttu-id="11b16-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11b16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b16-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11b16-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11b16-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11b16-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11b16-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b16-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b16-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11b16-118">See also</span></span>

- [<span data-ttu-id="11b16-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="11b16-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
