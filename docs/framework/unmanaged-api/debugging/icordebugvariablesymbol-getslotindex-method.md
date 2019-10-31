---
title: 'Método ICorDebugVariableSymbol:: GetSlotIndex'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: a7a7ecf7d3e3d0d2125b03d3604c44138a2be0cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120980"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="3f761-102">Método ICorDebugVariableSymbol:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="3f761-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="3f761-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="3f761-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f761-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f761-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f761-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f761-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="3f761-106">fora Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="3f761-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f761-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3f761-107">Return Value</span></span>  
 <span data-ttu-id="3f761-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="3f761-108">`S_OK` if successful.</span></span> <span data-ttu-id="3f761-109">`E_FAIL` se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="3f761-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f761-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f761-110">Remarks</span></span>  
 <span data-ttu-id="3f761-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar as informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="3f761-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f761-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3f761-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f761-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f761-113">Requirements</span></span>  
 <span data-ttu-id="3f761-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f761-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f761-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f761-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f761-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f761-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f761-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f761-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f761-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f761-118">See also</span></span>

- [<span data-ttu-id="3f761-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="3f761-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3f761-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3f761-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
