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
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790943"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="75561-102">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="75561-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="75561-103">Fornece um enumerador para as variáveis locais e argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="75561-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75561-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="75561-104">Methods</span></span>  
  
|<span data-ttu-id="75561-105">Método</span><span class="sxs-lookup"><span data-stu-id="75561-105">Method</span></span>|<span data-ttu-id="75561-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="75561-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75561-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="75561-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="75561-108">Obtém o número especificado de instâncias [ICorDebugVariableHome](icordebugvariablehome-interface.md) que contêm informações sobre as variáveis e os argumentos locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="75561-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75561-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="75561-109">Remarks</span></span>  
 <span data-ttu-id="75561-110">A interface `ICorDebugVariableHomeEnum` implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="75561-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="75561-111">Uma instância de `ICorDebugVariableHomeEnum` é populada com instâncias [ICorDebugVariableHome](icordebugvariablehome-interface.md) chamando o método [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="75561-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="75561-112">Cada instância de [ICorDebugVariableHome](icordebugvariablehome-interface.md) na coleção representa uma variável local ou um argumento em uma função.</span><span class="sxs-lookup"><span data-stu-id="75561-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="75561-113">Os objetos [ICorDebugVariableHome](icordebugvariablehome-interface.md) na coleção podem ser enumerados chamando o método [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="75561-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75561-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="75561-114">Requirements</span></span>  
 <span data-ttu-id="75561-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75561-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75561-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75561-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75561-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75561-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75561-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75561-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75561-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="75561-119">See also</span></span>

- [<span data-ttu-id="75561-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="75561-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="75561-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="75561-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
