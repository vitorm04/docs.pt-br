---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768817"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="796c6-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="796c6-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="796c6-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="796c6-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="796c6-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="796c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="796c6-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="796c6-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="796c6-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="796c6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="796c6-107">Return Value</span></span>  
 <span data-ttu-id="796c6-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="796c6-108">`S_OK` if successful.</span></span> <span data-ttu-id="796c6-109">`E_FAIL` Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="796c6-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="796c6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="796c6-110">Remarks</span></span>  
 <span data-ttu-id="796c6-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="796c6-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="796c6-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="796c6-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796c6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="796c6-113">Requirements</span></span>  
 <span data-ttu-id="796c6-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="796c6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796c6-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="796c6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="796c6-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="796c6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="796c6-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796c6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796c6-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="796c6-118">See also</span></span>

- [<span data-ttu-id="796c6-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="796c6-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="796c6-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="796c6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
