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
ms.openlocfilehash: 864cb893511bceabd61ce0064065b3866ce01dfe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212590"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="79f96-102">Método ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="79f96-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="79f96-103">Obtém o deslocamento a partir do registro de base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="79f96-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79f96-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79f96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79f96-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="79f96-106">[out] O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="79f96-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79f96-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="79f96-107">Return Value</span></span>  
 <span data-ttu-id="79f96-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="79f96-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="79f96-109">Valor</span><span class="sxs-lookup"><span data-stu-id="79f96-109">Value</span></span>|<span data-ttu-id="79f96-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="79f96-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="79f96-111">A variável está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="79f96-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="79f96-112">A variável não está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="79f96-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79f96-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79f96-113">Requirements</span></span>  
 <span data-ttu-id="79f96-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79f96-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79f96-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79f96-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79f96-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79f96-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79f96-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79f96-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f96-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79f96-118">See also</span></span>

- [<span data-ttu-id="79f96-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="79f96-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
