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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e67e4685320f56a4a6a8be2e3eb2e6c8065ce59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768999"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="a13fd-102">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="a13fd-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="a13fd-103">Fornece um enumerador para as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="a13fd-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a13fd-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a13fd-104">Methods</span></span>  
  
|<span data-ttu-id="a13fd-105">Método</span><span class="sxs-lookup"><span data-stu-id="a13fd-105">Method</span></span>|<span data-ttu-id="a13fd-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a13fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a13fd-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="a13fd-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="a13fd-108">Obtém o número especificado de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instâncias que contêm informações sobre as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="a13fd-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a13fd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a13fd-109">Remarks</span></span>  
 <span data-ttu-id="a13fd-110">O `ICorDebugVariableHomeEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a13fd-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a13fd-111">Uma `ICorDebugVariableHomeEnum` instância é preenchida com [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instâncias chamando o [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a13fd-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="a13fd-112">Cada [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância na coleção representa um argumento em uma função ou variável local.</span><span class="sxs-lookup"><span data-stu-id="a13fd-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="a13fd-113">O [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objetos na coleção podem ser enumerados chamando o [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a13fd-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a13fd-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a13fd-114">Requirements</span></span>  
 <span data-ttu-id="a13fd-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a13fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a13fd-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a13fd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a13fd-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a13fd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a13fd-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a13fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13fd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a13fd-119">See also</span></span>

- [<span data-ttu-id="a13fd-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="a13fd-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="a13fd-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a13fd-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
