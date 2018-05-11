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
ms.openlocfilehash: 2814f6164f383c36bb5b8e20ce8996b30eef0f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="f918b-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="f918b-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="f918b-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f918b-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f918b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f918b-104">Methods</span></span>  
  
|<span data-ttu-id="f918b-105">Método</span><span class="sxs-lookup"><span data-stu-id="f918b-105">Method</span></span>|<span data-ttu-id="f918b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f918b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f918b-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="f918b-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="f918b-108">Obtém o número de caracteres na cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="f918b-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="f918b-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="f918b-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="f918b-110">Obtém a cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="f918b-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f918b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f918b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f918b-112">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="f918b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f918b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f918b-113">Requirements</span></span>  
 <span data-ttu-id="f918b-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f918b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f918b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f918b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f918b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f918b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f918b-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f918b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f918b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f918b-118">See Also</span></span>  
 [<span data-ttu-id="f918b-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f918b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
