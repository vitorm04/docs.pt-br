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
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093742"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="f41ad-102">Método ICorDebugVariableHome::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="f41ad-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="f41ad-103">Obtém o índice de slot gerenciado de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="f41ad-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f41ad-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f41ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f41ad-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="f41ad-106">[out] Um ponteiro para o slot de índice de uma variável local.</span><span class="sxs-lookup"><span data-stu-id="f41ad-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f41ad-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f41ad-107">Return Value</span></span>  
 <span data-ttu-id="f41ad-108">O método retorna os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f41ad-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="f41ad-109">Valor</span><span class="sxs-lookup"><span data-stu-id="f41ad-109">Value</span></span>|<span data-ttu-id="f41ad-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f41ad-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="f41ad-111">A chamada de método retornou um valor de índice de slot no `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="f41ad-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="f41ad-112">O atual [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instância representa um argumento de função.</span><span class="sxs-lookup"><span data-stu-id="f41ad-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f41ad-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="f41ad-113">Remarks</span></span>  
 <span data-ttu-id="f41ad-114">O índice de slot pode ser usado para recuperar os metadados para essa variável local.</span><span class="sxs-lookup"><span data-stu-id="f41ad-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f41ad-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f41ad-115">Requirements</span></span>  
 <span data-ttu-id="f41ad-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f41ad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41ad-117">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f41ad-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f41ad-118">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f41ad-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f41ad-119">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f41ad-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f41ad-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f41ad-120">See also</span></span>

- [<span data-ttu-id="f41ad-121">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="f41ad-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
