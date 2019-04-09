---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138782"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="d11fc-102">Método ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="d11fc-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="d11fc-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="d11fc-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d11fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d11fc-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d11fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d11fc-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d11fc-106">[out] Um ponteiro para o índice de slot da variável local.</span><span class="sxs-lookup"><span data-stu-id="d11fc-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d11fc-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d11fc-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="d11fc-108">Se for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d11fc-108">if successful.</span></span> `E_FAIL` <span data-ttu-id="d11fc-109">Se a variável é um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="d11fc-109">if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d11fc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d11fc-110">Remarks</span></span>  
 <span data-ttu-id="d11fc-111">O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável</span><span class="sxs-lookup"><span data-stu-id="d11fc-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d11fc-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d11fc-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d11fc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d11fc-113">Requirements</span></span>  
 <span data-ttu-id="d11fc-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d11fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d11fc-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d11fc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d11fc-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d11fc-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d11fc-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d11fc-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d11fc-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d11fc-118">See also</span></span>

- [<span data-ttu-id="d11fc-119">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="d11fc-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d11fc-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d11fc-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
