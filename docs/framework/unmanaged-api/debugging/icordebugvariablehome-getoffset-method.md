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
ms.openlocfilehash: 687c3bb441c2a12529c873b4fa5f9283b9326a40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659063"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="4b05b-102">Método ICorDebugVariableHome::GetOffset</span><span class="sxs-lookup"><span data-stu-id="4b05b-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="4b05b-103">Obtém o deslocamento a partir do registro de base para uma variável.</span><span class="sxs-lookup"><span data-stu-id="4b05b-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b05b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b05b-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b05b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b05b-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="4b05b-106">[out] O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="4b05b-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b05b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4b05b-107">Return Value</span></span>  
 <span data-ttu-id="4b05b-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="4b05b-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="4b05b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="4b05b-109">Value</span></span>|<span data-ttu-id="4b05b-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b05b-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="4b05b-111">A variável está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="4b05b-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="4b05b-112">A variável não está em um local de memória relativo ao registro.</span><span class="sxs-lookup"><span data-stu-id="4b05b-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b05b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b05b-113">Requirements</span></span>  
 <span data-ttu-id="4b05b-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b05b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b05b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b05b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b05b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b05b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b05b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b05b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b05b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b05b-118">See also</span></span>
- [<span data-ttu-id="4b05b-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="4b05b-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
