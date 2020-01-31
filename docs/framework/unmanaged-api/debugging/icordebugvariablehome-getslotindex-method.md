---
title: 'Método ICorDebugVariableHome:: GetSlotIndex'
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
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790967"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="d4a45-102">Método ICorDebugVariableHome:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="d4a45-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="d4a45-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="d4a45-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4a45-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4a45-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4a45-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4a45-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d4a45-106">fora Um ponteiro para o índice de slot de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="d4a45-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4a45-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d4a45-107">Return Value</span></span>  
 <span data-ttu-id="d4a45-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4a45-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d4a45-109">Value</span><span class="sxs-lookup"><span data-stu-id="d4a45-109">Value</span></span>|<span data-ttu-id="d4a45-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4a45-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d4a45-111">A chamada de método retornou um valor de índice de slot em `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="d4a45-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d4a45-112">A instância [ICorDebugVariableHome](icordebugvariablehome-interface.md) atual representa um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="d4a45-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4a45-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4a45-113">Remarks</span></span>  
 <span data-ttu-id="d4a45-114">O slot-index pode ser usado para recuperar os metadados para essa variável local.</span><span class="sxs-lookup"><span data-stu-id="d4a45-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4a45-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d4a45-115">Requirements</span></span>  
 <span data-ttu-id="d4a45-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4a45-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4a45-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4a45-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4a45-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4a45-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4a45-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4a45-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a45-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="d4a45-120">See also</span></span>

- [<span data-ttu-id="d4a45-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d4a45-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
