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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212590"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="a6414-102">Método ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="a6414-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="a6414-103">Obtém o deslocamento a partir do registro de base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="a6414-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6414-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6414-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6414-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6414-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="a6414-106">[out] O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="a6414-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6414-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a6414-107">Return Value</span></span>  
 <span data-ttu-id="a6414-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="a6414-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="a6414-109">Valor</span><span class="sxs-lookup"><span data-stu-id="a6414-109">Value</span></span>|<span data-ttu-id="a6414-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6414-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="a6414-111">A variável está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="a6414-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="a6414-112">A variável não está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="a6414-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6414-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6414-113">Requirements</span></span>  
 <span data-ttu-id="a6414-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6414-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6414-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6414-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6414-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6414-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a6414-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a6414-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a6414-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6414-118">See also</span></span>

- [<span data-ttu-id="a6414-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="a6414-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
