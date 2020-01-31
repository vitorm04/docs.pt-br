---
title: 'Método ICorDebugVariableSymbol:: GetSlotIndex'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790888"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="b4538-102">Método ICorDebugVariableSymbol:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="b4538-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="b4538-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="b4538-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4538-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4538-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4538-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4538-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="b4538-106">fora Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="b4538-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4538-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b4538-107">Return Value</span></span>  
 <span data-ttu-id="b4538-108">`S_OK` se bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="b4538-108">`S_OK` if successful.</span></span> <span data-ttu-id="b4538-109">`E_FAIL` se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="b4538-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4538-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4538-110">Remarks</span></span>  
 <span data-ttu-id="b4538-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar as informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="b4538-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4538-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b4538-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4538-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="b4538-113">Requirements</span></span>  
 <span data-ttu-id="b4538-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4538-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4538-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4538-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4538-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4538-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4538-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4538-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4538-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="b4538-118">See also</span></span>

- [<span data-ttu-id="b4538-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="b4538-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="b4538-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b4538-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
