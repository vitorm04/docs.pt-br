---
title: 'Método ICorDebugVariableSymbol:: GetSlotIndex'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58bb2cc63f2336ca9cfbed8ebeac0d607c18b2c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968152"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="d2693-102">Método ICorDebugVariableSymbol:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="d2693-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="d2693-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="d2693-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2693-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2693-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2693-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2693-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d2693-106">fora Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="d2693-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2693-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d2693-107">Return Value</span></span>  
 <span data-ttu-id="d2693-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d2693-108">`S_OK` if successful.</span></span> <span data-ttu-id="d2693-109">`E_FAIL`se a variável for um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="d2693-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2693-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2693-110">Remarks</span></span>  
 <span data-ttu-id="d2693-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar as informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="d2693-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2693-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d2693-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2693-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d2693-113">Requirements</span></span>  
 <span data-ttu-id="d2693-114">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2693-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2693-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2693-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2693-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2693-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2693-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2693-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2693-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2693-118">See also</span></span>

- [<span data-ttu-id="d2693-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="d2693-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d2693-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d2693-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
