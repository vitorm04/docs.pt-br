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
ms.openlocfilehash: d5962de8cc2762f6ecf4864c5255da0fe83918e4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396526"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="69119-102">Interface ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="69119-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="69119-103">Fornece um enumerador para as variáveis locais e argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="69119-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69119-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="69119-104">Methods</span></span>  
  
|<span data-ttu-id="69119-105">Método</span><span class="sxs-lookup"><span data-stu-id="69119-105">Method</span></span>|<span data-ttu-id="69119-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="69119-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69119-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="69119-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="69119-108">Obtém o número especificado de instâncias [ICorDebugVariableHome](icordebugvariablehome-interface.md) que contêm informações sobre as variáveis e os argumentos locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="69119-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69119-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="69119-109">Remarks</span></span>  
 <span data-ttu-id="69119-110">A `ICorDebugVariableHomeEnum` interface implementa a interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="69119-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="69119-111">Uma `ICorDebugVariableHomeEnum` instância é populada com instâncias [ICorDebugVariableHome](icordebugvariablehome-interface.md) chamando o método [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="69119-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="69119-112">Cada instância de [ICorDebugVariableHome](icordebugvariablehome-interface.md) na coleção representa uma variável local ou um argumento em uma função.</span><span class="sxs-lookup"><span data-stu-id="69119-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="69119-113">Os objetos [ICorDebugVariableHome](icordebugvariablehome-interface.md) na coleção podem ser enumerados chamando o método [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="69119-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69119-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69119-114">Requirements</span></span>  
 <span data-ttu-id="69119-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69119-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69119-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69119-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69119-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69119-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69119-118">**.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69119-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69119-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="69119-119">See also</span></span>

- [<span data-ttu-id="69119-120">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="69119-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="69119-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="69119-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
