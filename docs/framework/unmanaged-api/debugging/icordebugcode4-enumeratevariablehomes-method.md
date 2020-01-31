---
title: 'Método ICorDebugCode4:: EnumerateVariableHomes'
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
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784082"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a><span data-ttu-id="713c7-102">Método ICorDebugCode4:: EnumerateVariableHomes</span><span class="sxs-lookup"><span data-stu-id="713c7-102">ICorDebugCode4::EnumerateVariableHomes Method</span></span>
<span data-ttu-id="713c7-103">Obtém um enumerador para as variáveis locais e argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="713c7-103">Gets an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="713c7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="713c7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="713c7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="713c7-106">Um ponteiro para o endereço de um objeto de interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) que é um enumerador para as variáveis locais e argumentos em uma função.</span><span class="sxs-lookup"><span data-stu-id="713c7-106">A pointer to the address of an [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object that is an enumerator for the local variables and arguments in a function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="713c7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="713c7-107">Remarks</span></span>  
 <span data-ttu-id="713c7-108">O objeto de interface [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) é um enumerador padrão derivado da interface "ICorDebugEnum" que permite enumerar objetos [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="713c7-108">The [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md) interface object is a standard enumerator derived from the "ICorDebugEnum" interface that allows you to enumerate [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects.</span></span> <span data-ttu-id="713c7-109">A coleção pode incluir vários objetos [ICorDebugVariableHome](icordebugvariablehome-interface.md) para o mesmo índice de slot ou de argumento se eles tiverem diferentes residências em pontos diferentes na função.</span><span class="sxs-lookup"><span data-stu-id="713c7-109">The collection may include multiple [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects for the same slot or      argument index if they have different homes at different points in the      function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="713c7-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="713c7-110">Requirements</span></span>  
 <span data-ttu-id="713c7-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="713c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="713c7-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="713c7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="713c7-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="713c7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="713c7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="713c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713c7-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="713c7-115">See also</span></span>

- [<span data-ttu-id="713c7-116">Interface ICorDebugCode4</span><span class="sxs-lookup"><span data-stu-id="713c7-116">ICorDebugCode4 Interface</span></span>](icordebugcode4-interface.md)
- [<span data-ttu-id="713c7-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="713c7-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
