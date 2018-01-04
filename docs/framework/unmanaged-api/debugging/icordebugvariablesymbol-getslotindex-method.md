---
title: "Método ICorDebugVariableSymbol::GetSlotIndex"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb84e529768e0be44883511bb89703a4c3199df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="b671d-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="b671d-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="b671d-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="b671d-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b671d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b671d-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b671d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b671d-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="b671d-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="b671d-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b671d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b671d-107">Return Value</span></span>  
 <span data-ttu-id="b671d-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b671d-108">`S_OK` if successful.</span></span> <span data-ttu-id="b671d-109">`E_FAIL`Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="b671d-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b671d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b671d-110">Remarks</span></span>  
 <span data-ttu-id="b671d-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="b671d-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b671d-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b671d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b671d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b671d-113">Requirements</span></span>  
 <span data-ttu-id="b671d-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b671d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b671d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b671d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b671d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b671d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b671d-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b671d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b671d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b671d-118">See Also</span></span>  
 [<span data-ttu-id="b671d-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="b671d-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="b671d-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b671d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
