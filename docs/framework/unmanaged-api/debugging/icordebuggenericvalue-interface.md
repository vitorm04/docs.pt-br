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
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209780"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="4013e-102">Interface ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="4013e-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="4013e-103">Uma subclasse de "ICorDebugValue" que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="4013e-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="4013e-104">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="4013e-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4013e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4013e-105">Methods</span></span>  
  
|<span data-ttu-id="4013e-106">Método</span><span class="sxs-lookup"><span data-stu-id="4013e-106">Method</span></span>|<span data-ttu-id="4013e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4013e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4013e-108">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="4013e-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="4013e-109">Copia o valor no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="4013e-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="4013e-110">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="4013e-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="4013e-111">Copia um novo valor do buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="4013e-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4013e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="4013e-112">Remarks</span></span>  
 <span data-ttu-id="4013e-113">`ICorDebugGenericValue`é uma subinterface porque ela não é remota.</span><span class="sxs-lookup"><span data-stu-id="4013e-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="4013e-114">Para tipos de referência, o valor é a referência em vez do conteúdo da referência.</span><span class="sxs-lookup"><span data-stu-id="4013e-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="4013e-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4013e-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4013e-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4013e-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4013e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4013e-117">Requirements</span></span>  
 <span data-ttu-id="4013e-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4013e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4013e-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4013e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4013e-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4013e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4013e-121">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4013e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4013e-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="4013e-122">See also</span></span>

- [<span data-ttu-id="4013e-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4013e-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
