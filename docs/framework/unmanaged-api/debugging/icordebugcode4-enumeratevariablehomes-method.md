---
title: Método ICorDebugCode4::EnumerateVariableHomes
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e6acdf6996f437c85b629b0af886287b1aef03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748562"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="5a025-102">Método ICorDebugCode4::EnumerateVariableHomes</span><span class="sxs-lookup"><span data-stu-id="5a025-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="5a025-103">Obtém um enumerador para os argumentos e variáveis locais em uma função.</span><span class="sxs-lookup"><span data-stu-id="5a025-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a025-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a025-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a025-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a025-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5a025-106">Um ponteiro para o endereço de um [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objeto de interface que é um enumerador para as variáveis locais e os argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="5a025-106">A pointer to the address of an [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a025-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a025-107">Remarks</span></span>  
 <span data-ttu-id="5a025-108">O [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) objeto de interface é um enumerador padrão derivado da interface "ICorDebugEnum" que permite que você enumere [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="5a025-108">The [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="5a025-109">A coleção pode incluir vários [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objetos para o mesmo índice de slot ou argumento se eles tiverem residências diferentes em diferentes pontos na função.</span><span class="sxs-lookup"><span data-stu-id="5a025-109">The collection may include multiple [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a025-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a025-110">Requirements</span></span>  
 <span data-ttu-id="5a025-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a025-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a025-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a025-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a025-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a025-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a025-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a025-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a025-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a025-115">See also</span></span>

- [<span data-ttu-id="5a025-116">Interface ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="5a025-116">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [<span data-ttu-id="5a025-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5a025-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
