---
title: Método ICorDebugVariableHome::GetSlotIndex
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61014e067b2afb8b7e4be0488ed6a3c7f1bd6fc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="20e50-102">Método ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="20e50-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="20e50-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="20e50-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20e50-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20e50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="20e50-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="20e50-106">[out] Um ponteiro para o slot de índice de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="20e50-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20e50-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="20e50-107">Return Value</span></span>  
 <span data-ttu-id="20e50-108">O método retorna os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="20e50-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="20e50-109">Valor</span><span class="sxs-lookup"><span data-stu-id="20e50-109">Value</span></span>|<span data-ttu-id="20e50-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="20e50-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="20e50-111">A chamada do método retornou um valor de índice de slot no `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="20e50-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="20e50-112">Atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="20e50-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20e50-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="20e50-113">Remarks</span></span>  
 <span data-ttu-id="20e50-114">O índice de slot pode ser usado para recuperar os metadados da variável local.</span><span class="sxs-lookup"><span data-stu-id="20e50-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e50-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20e50-115">Requirements</span></span>  
 <span data-ttu-id="20e50-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e50-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e50-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20e50-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20e50-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20e50-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20e50-119">**Versões do .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e50-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e50-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20e50-120">See Also</span></span>  
 [<span data-ttu-id="20e50-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="20e50-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
