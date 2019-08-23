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
ms.openlocfilehash: 1cfaf886d09d843f4dbf61af55a9388454b050ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957422"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="22f57-102">Interface ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="22f57-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="22f57-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="22f57-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22f57-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="22f57-104">Methods</span></span>  
  
|<span data-ttu-id="22f57-105">Método</span><span class="sxs-lookup"><span data-stu-id="22f57-105">Method</span></span>|<span data-ttu-id="22f57-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="22f57-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22f57-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="22f57-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="22f57-108">Obtém o número de caracteres na cadeia de caracteres referenciada `ICorDebugStringValue`por isso.</span><span class="sxs-lookup"><span data-stu-id="22f57-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="22f57-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="22f57-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="22f57-110">Obtém a cadeia de caracteres referenciada por isso `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="22f57-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f57-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="22f57-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22f57-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="22f57-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f57-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22f57-113">Requirements</span></span>  
 <span data-ttu-id="22f57-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22f57-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f57-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22f57-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22f57-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22f57-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22f57-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22f57-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f57-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f57-118">See also</span></span>

- [<span data-ttu-id="22f57-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="22f57-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
