---
title: Interface ICorDebugClass2
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: ff15297eb479f7474c9f07123a29263fb4da3205
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893981"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="3dfd2-102">Interface ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="3dfd2-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="3dfd2-103">Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="3dfd2-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="3dfd2-104">Essa interface estende [ICorDebugClass](icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3dfd2-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3dfd2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3dfd2-105">Methods</span></span>  
  
|<span data-ttu-id="3dfd2-106">Método</span><span class="sxs-lookup"><span data-stu-id="3dfd2-106">Method</span></span>|<span data-ttu-id="3dfd2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3dfd2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3dfd2-108">Método GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="3dfd2-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="3dfd2-109">Obtém a declaração de tipo para esta classe.</span><span class="sxs-lookup"><span data-stu-id="3dfd2-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="3dfd2-110">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="3dfd2-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="3dfd2-111">Para cada método dessa classe, define um valor que indica se o método é um código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="3dfd2-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dfd2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="3dfd2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3dfd2-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="3dfd2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dfd2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3dfd2-114">Requirements</span></span>  
 <span data-ttu-id="3dfd2-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dfd2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dfd2-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dfd2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dfd2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dfd2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dfd2-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dfd2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dfd2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3dfd2-119">See also</span></span>

- [<span data-ttu-id="3dfd2-120">Interface ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="3dfd2-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="3dfd2-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3dfd2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
