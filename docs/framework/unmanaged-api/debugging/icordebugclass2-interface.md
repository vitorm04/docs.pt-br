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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 015085cff23028814937dfef9aea19af7438b4f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173804"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="25b2c-102">Interface ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="25b2c-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="25b2c-103">Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="25b2c-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="25b2c-104">Essa interface estende [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="25b2c-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25b2c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="25b2c-105">Methods</span></span>  
  
|<span data-ttu-id="25b2c-106">Método</span><span class="sxs-lookup"><span data-stu-id="25b2c-106">Method</span></span>|<span data-ttu-id="25b2c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="25b2c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25b2c-108">Método GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="25b2c-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="25b2c-109">Obtém a declaração de tipo para esta classe.</span><span class="sxs-lookup"><span data-stu-id="25b2c-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="25b2c-110">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="25b2c-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="25b2c-111">Para cada método dessa classe, define um valor que indica se o método é o código definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="25b2c-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25b2c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="25b2c-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25b2c-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="25b2c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b2c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25b2c-114">Requirements</span></span>  
 <span data-ttu-id="25b2c-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b2c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b2c-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25b2c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25b2c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25b2c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25b2c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b2c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b2c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25b2c-119">See also</span></span>

- [<span data-ttu-id="25b2c-120">Interface ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="25b2c-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="25b2c-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="25b2c-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
