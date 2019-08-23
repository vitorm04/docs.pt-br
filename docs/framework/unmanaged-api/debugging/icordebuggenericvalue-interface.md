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
ms.openlocfilehash: 36c2ed5529151a7ea18ccaffc2202ad6c69bcbd9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910226"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="501ff-102">Interface ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="501ff-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="501ff-103">Uma subclasse de "ICorDebugValue" que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="501ff-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="501ff-104">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="501ff-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="501ff-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="501ff-105">Methods</span></span>  
  
|<span data-ttu-id="501ff-106">Método</span><span class="sxs-lookup"><span data-stu-id="501ff-106">Method</span></span>|<span data-ttu-id="501ff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="501ff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="501ff-108">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="501ff-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="501ff-109">Copia o valor no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="501ff-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="501ff-110">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="501ff-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="501ff-111">Copia um novo valor do buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="501ff-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="501ff-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="501ff-112">Remarks</span></span>  
 <span data-ttu-id="501ff-113">`ICorDebugGenericValue`é uma subinterface porque ela não é remota.</span><span class="sxs-lookup"><span data-stu-id="501ff-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="501ff-114">Para tipos de referência, o valor é a referência em vez do conteúdo da referência.</span><span class="sxs-lookup"><span data-stu-id="501ff-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="501ff-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="501ff-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="501ff-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="501ff-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="501ff-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="501ff-117">Requirements</span></span>  
 <span data-ttu-id="501ff-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="501ff-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="501ff-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="501ff-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="501ff-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="501ff-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="501ff-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="501ff-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501ff-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="501ff-122">See also</span></span>

- [<span data-ttu-id="501ff-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="501ff-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
