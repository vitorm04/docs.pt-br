---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09b50af49f8379539773d2000a6c1f8222fee875
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563828"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="da565-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="da565-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="da565-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="da565-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da565-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da565-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da565-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="da565-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="da565-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="da565-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da565-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="da565-107">Return Value</span></span>  
 <span data-ttu-id="da565-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="da565-108">`S_OK` if successful.</span></span> <span data-ttu-id="da565-109">`E_FAIL` Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="da565-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da565-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="da565-110">Remarks</span></span>  
 <span data-ttu-id="da565-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="da565-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da565-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da565-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da565-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da565-113">Requirements</span></span>  
 <span data-ttu-id="da565-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da565-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da565-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da565-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da565-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da565-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da565-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da565-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da565-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da565-118">See also</span></span>
- [<span data-ttu-id="da565-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="da565-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="da565-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="da565-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
