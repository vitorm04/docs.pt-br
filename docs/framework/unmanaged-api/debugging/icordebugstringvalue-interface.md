---
title: ICorDebugStringValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue
helpviewer_keywords: ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03ae6fba5d880b11baac695866853e0b3a4d8cc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="9e282-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="9e282-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="9e282-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e282-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e282-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9e282-104">Methods</span></span>  
  
|<span data-ttu-id="9e282-105">Método</span><span class="sxs-lookup"><span data-stu-id="9e282-105">Method</span></span>|<span data-ttu-id="9e282-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e282-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e282-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="9e282-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="9e282-108">Obtém o número de caracteres na cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="9e282-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="9e282-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="9e282-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="9e282-110">Obtém a cadeia de caracteres referenciada por este `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="9e282-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e282-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e282-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e282-112">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="9e282-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e282-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e282-113">Requirements</span></span>  
 <span data-ttu-id="9e282-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e282-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e282-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e282-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e282-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e282-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e282-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e282-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e282-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e282-118">See Also</span></span>  
 [<span data-ttu-id="9e282-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="9e282-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
