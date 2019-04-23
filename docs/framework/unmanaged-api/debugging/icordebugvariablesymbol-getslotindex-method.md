---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138782"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="51061-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="51061-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="51061-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="51061-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51061-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51061-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51061-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="51061-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="51061-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="51061-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51061-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="51061-107">Return Value</span></span>  
 <span data-ttu-id="51061-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="51061-108">`S_OK` if successful.</span></span> <span data-ttu-id="51061-109">`E_FAIL` Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="51061-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51061-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="51061-110">Remarks</span></span>  
 <span data-ttu-id="51061-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="51061-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51061-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="51061-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51061-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51061-113">Requirements</span></span>  
 <span data-ttu-id="51061-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51061-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51061-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51061-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51061-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51061-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51061-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51061-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51061-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51061-118">See also</span></span>

- [<span data-ttu-id="51061-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="51061-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="51061-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="51061-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
