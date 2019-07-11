---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84d9e30a2baf08f6b7ff530f2fce049d49386a60
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774849"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="42617-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="42617-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="42617-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="42617-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42617-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42617-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42617-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="42617-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="42617-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="42617-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42617-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="42617-107">Return Value</span></span>  
 <span data-ttu-id="42617-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="42617-108">`S_OK` if successful.</span></span> <span data-ttu-id="42617-109">`E_FAIL` Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="42617-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42617-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="42617-110">Remarks</span></span>  
 <span data-ttu-id="42617-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="42617-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42617-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="42617-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42617-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="42617-113">Requirements</span></span>  
 <span data-ttu-id="42617-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42617-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42617-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42617-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42617-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42617-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42617-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42617-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42617-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42617-118">See also</span></span>

- [<span data-ttu-id="42617-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="42617-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="42617-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="42617-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
