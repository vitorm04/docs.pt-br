---
title: Método ICorDebugVariableHome::GetOffset
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fdab81d499fe1508493cb0bf05a1787974a9d01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774531"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="4798e-102">Método ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="4798e-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="4798e-103">Obtém o deslocamento a partir do registro de base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="4798e-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4798e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4798e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4798e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4798e-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="4798e-106">[out] O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="4798e-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4798e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4798e-107">Return Value</span></span>  
 <span data-ttu-id="4798e-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="4798e-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="4798e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="4798e-109">Value</span></span>|<span data-ttu-id="4798e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4798e-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="4798e-111">A variável está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="4798e-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="4798e-112">A variável não está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="4798e-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4798e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4798e-113">Requirements</span></span>  
 <span data-ttu-id="4798e-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4798e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4798e-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4798e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4798e-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4798e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4798e-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4798e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4798e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4798e-118">See also</span></span>

- [<span data-ttu-id="4798e-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="4798e-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
