---
title: 'Método ICorDebugVariableSymbol:: GetSlotIndex'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 251a978e96ff396d0d9d9282ded7f8a25ae0ba0b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397088"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="3009d-102">Método ICorDebugVariableSymbol:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="3009d-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="3009d-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="3009d-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3009d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3009d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3009d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3009d-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="3009d-106">fora Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="3009d-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3009d-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3009d-107">Return Value</span></span>  
 <span data-ttu-id="3009d-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="3009d-108">`S_OK` if successful.</span></span> <span data-ttu-id="3009d-109">`E_FAIL`se a variável for um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="3009d-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3009d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3009d-110">Remarks</span></span>  
 <span data-ttu-id="3009d-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar as informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="3009d-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3009d-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3009d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3009d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3009d-113">Requirements</span></span>  
 <span data-ttu-id="3009d-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3009d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3009d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3009d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3009d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3009d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3009d-117">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3009d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3009d-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="3009d-118">See also</span></span>

- [<span data-ttu-id="3009d-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="3009d-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3009d-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3009d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
