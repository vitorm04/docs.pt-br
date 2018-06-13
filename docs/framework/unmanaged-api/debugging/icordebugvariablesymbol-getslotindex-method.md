---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420616"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="9754c-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="9754c-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="9754c-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="9754c-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9754c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9754c-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9754c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9754c-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="9754c-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="9754c-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9754c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9754c-107">Return Value</span></span>  
 <span data-ttu-id="9754c-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="9754c-108">`S_OK` if successful.</span></span> <span data-ttu-id="9754c-109">`E_FAIL` Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="9754c-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9754c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9754c-110">Remarks</span></span>  
 <span data-ttu-id="9754c-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="9754c-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9754c-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9754c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9754c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9754c-113">Requirements</span></span>  
 <span data-ttu-id="9754c-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9754c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9754c-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9754c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9754c-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9754c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9754c-117">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9754c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9754c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9754c-118">See Also</span></span>  
 [<span data-ttu-id="9754c-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="9754c-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="9754c-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9754c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
