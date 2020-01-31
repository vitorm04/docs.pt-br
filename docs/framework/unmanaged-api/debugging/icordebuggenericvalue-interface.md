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
ms.openlocfilehash: e60d4b128bf03ff81863e0c95815b2c204807583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794464"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="05e4f-102">Interface ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="05e4f-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="05e4f-103">Uma subclasse de "ICorDebugValue" que se aplica a todos os valores.</span><span class="sxs-lookup"><span data-stu-id="05e4f-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="05e4f-104">Essa interface fornece métodos Get e Set para o valor.</span><span class="sxs-lookup"><span data-stu-id="05e4f-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05e4f-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="05e4f-105">Methods</span></span>  
  
|<span data-ttu-id="05e4f-106">Método</span><span class="sxs-lookup"><span data-stu-id="05e4f-106">Method</span></span>|<span data-ttu-id="05e4f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="05e4f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05e4f-108">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="05e4f-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="05e4f-109">Copia o valor no buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="05e4f-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="05e4f-110">Método SetValue</span><span class="sxs-lookup"><span data-stu-id="05e4f-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="05e4f-111">Copia um novo valor do buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="05e4f-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05e4f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="05e4f-112">Remarks</span></span>  
 <span data-ttu-id="05e4f-113">`ICorDebugGenericValue` é uma subinterface porque ela não é remota.</span><span class="sxs-lookup"><span data-stu-id="05e4f-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="05e4f-114">Para tipos de referência, o valor é a referência em vez do conteúdo da referência.</span><span class="sxs-lookup"><span data-stu-id="05e4f-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="05e4f-115">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="05e4f-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05e4f-116">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="05e4f-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05e4f-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="05e4f-117">Requirements</span></span>  
 <span data-ttu-id="05e4f-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05e4f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05e4f-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05e4f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05e4f-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05e4f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05e4f-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05e4f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e4f-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="05e4f-122">See also</span></span>

- [<span data-ttu-id="05e4f-123">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="05e4f-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
