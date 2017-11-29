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
ms.openlocfilehash: d632bc792152afcfc94b51235dc0699fb3efc245
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="7b027-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="7b027-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="7b027-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="7b027-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b027-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b027-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b027-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7b027-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="7b027-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="7b027-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b027-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7b027-107">Return Value</span></span>  
 <span data-ttu-id="7b027-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="7b027-108">`S_OK` if successful.</span></span> <span data-ttu-id="7b027-109">`E_FAIL`Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="7b027-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b027-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b027-110">Remarks</span></span>  
 <span data-ttu-id="7b027-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="7b027-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b027-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7b027-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b027-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b027-113">Requirements</span></span>  
 <span data-ttu-id="7b027-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b027-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b027-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b027-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b027-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b027-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b027-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b027-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b027-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b027-118">See Also</span></span>  
 [<span data-ttu-id="7b027-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="7b027-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="7b027-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="7b027-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
