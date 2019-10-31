---
title: Interface ICorDebugVariableHomeEnum
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: a9b65449747fde42f9cd770e33741ef34d33fbb8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121032"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="f79b9-102">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="f79b9-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="f79b9-103">Fornece um enumerador para as variáveis locais e argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="f79b9-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f79b9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f79b9-104">Methods</span></span>  
  
|<span data-ttu-id="f79b9-105">Método</span><span class="sxs-lookup"><span data-stu-id="f79b9-105">Method</span></span>|<span data-ttu-id="f79b9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f79b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f79b9-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="f79b9-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="f79b9-108">Obtém o número especificado de instâncias [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) que contêm informações sobre as variáveis e os argumentos locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="f79b9-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f79b9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f79b9-109">Remarks</span></span>  
 <span data-ttu-id="f79b9-110">A interface `ICorDebugVariableHomeEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="f79b9-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="f79b9-111">Uma instância de `ICorDebugVariableHomeEnum` é populada com instâncias [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) chamando o método [ICorDebugCode4:: EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f79b9-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="f79b9-112">Cada instância de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) na coleção representa uma variável local ou um argumento em uma função.</span><span class="sxs-lookup"><span data-stu-id="f79b9-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="f79b9-113">Os objetos [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) na coleção podem ser enumerados chamando o método [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f79b9-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79b9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f79b9-114">Requirements</span></span>  
 <span data-ttu-id="f79b9-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f79b9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f79b9-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f79b9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f79b9-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f79b9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f79b9-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f79b9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f79b9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f79b9-119">See also</span></span>

- [<span data-ttu-id="f79b9-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="f79b9-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="f79b9-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f79b9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
