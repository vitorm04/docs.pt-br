---
title: Interface ICorDebugVariableHomeEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum
helpviewer_keywords: ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e64a52ca70606f83138b636f7ccb62ba18908f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="bafde-102">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="bafde-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="bafde-103">Fornece um enumerador para a variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="bafde-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bafde-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bafde-104">Methods</span></span>  
  
|<span data-ttu-id="bafde-105">Método</span><span class="sxs-lookup"><span data-stu-id="bafde-105">Method</span></span>|<span data-ttu-id="bafde-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bafde-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bafde-107">Próximo método</span><span class="sxs-lookup"><span data-stu-id="bafde-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="bafde-108">Obtém o número especificado de [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instâncias que contêm informações sobre as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="bafde-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bafde-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bafde-109">Remarks</span></span>  
 <span data-ttu-id="bafde-110">O `ICorDebugVariableHomeEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bafde-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="bafde-111">Um `ICorDebugVariableHomeEnum` instância é populada com [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instâncias chamando o [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bafde-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="bafde-112">Cada [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância na coleção representa um argumento em uma função ou variável local.</span><span class="sxs-lookup"><span data-stu-id="bafde-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="bafde-113">O [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objetos na coleção podem ser enumerados chamando o [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bafde-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bafde-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bafde-114">Requirements</span></span>  
 <span data-ttu-id="bafde-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bafde-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bafde-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bafde-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bafde-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bafde-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bafde-118">**Versões do .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bafde-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafde-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bafde-119">See Also</span></span>  
 [<span data-ttu-id="bafde-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="bafde-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="bafde-121">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="bafde-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
