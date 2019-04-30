---
title: Interface ICorDebugGenericValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988670"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="d5f6f-102">Interface ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="d5f6f-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="d5f6f-103">Uma subclasse de "ICorDebugValue" que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="d5f6f-104">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5f6f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d5f6f-105">Methods</span></span>  
  
|<span data-ttu-id="d5f6f-106">Método</span><span class="sxs-lookup"><span data-stu-id="d5f6f-106">Method</span></span>|<span data-ttu-id="d5f6f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d5f6f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5f6f-108">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="d5f6f-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="d5f6f-109">Copia o valor para o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="d5f6f-110">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="d5f6f-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="d5f6f-111">Copia um novo valor de buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5f6f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5f6f-112">Remarks</span></span>  
 <span data-ttu-id="d5f6f-113">`ICorDebugGenericValue` é uma interface de subpropriedades porque ele é não remotas.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="d5f6f-114">Para tipos de referência, o valor é a referência em vez do conteúdo de referência.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="d5f6f-115">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5f6f-116">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="d5f6f-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5f6f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5f6f-117">Requirements</span></span>  
 <span data-ttu-id="d5f6f-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5f6f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f6f-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5f6f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5f6f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5f6f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5f6f-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5f6f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5f6f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5f6f-122">See also</span></span>

- [<span data-ttu-id="d5f6f-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d5f6f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
