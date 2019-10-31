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
ms.openlocfilehash: cb2ab28824d209dd1eed627600e30e9ddb0d7c7a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125717"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="84158-102">Interface ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="84158-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="84158-103">Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="84158-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="84158-104">Essa interface estende [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="84158-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84158-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="84158-105">Methods</span></span>  
  
|<span data-ttu-id="84158-106">Método</span><span class="sxs-lookup"><span data-stu-id="84158-106">Method</span></span>|<span data-ttu-id="84158-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="84158-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84158-108">Método GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="84158-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="84158-109">Obtém a declaração de tipo para esta classe.</span><span class="sxs-lookup"><span data-stu-id="84158-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="84158-110">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="84158-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="84158-111">Para cada método dessa classe, define um valor que indica se o método é um código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="84158-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84158-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="84158-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84158-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="84158-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84158-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84158-114">Requirements</span></span>  
 <span data-ttu-id="84158-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84158-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84158-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84158-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84158-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84158-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84158-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84158-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84158-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84158-119">See also</span></span>

- [<span data-ttu-id="84158-120">Interface ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="84158-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="84158-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="84158-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
