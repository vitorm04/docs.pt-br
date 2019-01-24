---
title: ICorDebugStringValue Interface1
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
ms.openlocfilehash: b9160b9013481de294e6c8dd032cfa2d0ebb405d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596833"
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="77c0f-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="77c0f-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="77c0f-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="77c0f-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77c0f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="77c0f-104">Methods</span></span>  
  
|<span data-ttu-id="77c0f-105">Método</span><span class="sxs-lookup"><span data-stu-id="77c0f-105">Method</span></span>|<span data-ttu-id="77c0f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="77c0f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77c0f-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="77c0f-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="77c0f-108">Obtém o número de caracteres na cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="77c0f-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="77c0f-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="77c0f-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="77c0f-110">Obtém a cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="77c0f-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77c0f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="77c0f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77c0f-112">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="77c0f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77c0f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77c0f-113">Requirements</span></span>  
 <span data-ttu-id="77c0f-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77c0f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77c0f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77c0f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77c0f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77c0f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77c0f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77c0f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77c0f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77c0f-118">See also</span></span>
- [<span data-ttu-id="77c0f-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="77c0f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
