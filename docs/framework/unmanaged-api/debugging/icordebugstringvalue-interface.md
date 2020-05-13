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
ms.openlocfilehash: 5537a48fd085ce98de855fa1ec0913e2637e58e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376190"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="fa9c2-102">Interface ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="fa9c2-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="fa9c2-103">Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa9c2-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fa9c2-104">Methods</span></span>  
  
|<span data-ttu-id="fa9c2-105">Método</span><span class="sxs-lookup"><span data-stu-id="fa9c2-105">Method</span></span>|<span data-ttu-id="fa9c2-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa9c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa9c2-107">Método GetLength</span><span class="sxs-lookup"><span data-stu-id="fa9c2-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="fa9c2-108">Obtém o número de caracteres na cadeia de caracteres referenciada por isso `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="fa9c2-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="fa9c2-109">Método GetString</span><span class="sxs-lookup"><span data-stu-id="fa9c2-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="fa9c2-110">Obtém a cadeia de caracteres referenciada por isso `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="fa9c2-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa9c2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa9c2-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa9c2-112">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="fa9c2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa9c2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa9c2-113">Requirements</span></span>  
 <span data-ttu-id="fa9c2-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa9c2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa9c2-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa9c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa9c2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa9c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa9c2-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa9c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9c2-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="fa9c2-118">See also</span></span>

- [<span data-ttu-id="fa9c2-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fa9c2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
