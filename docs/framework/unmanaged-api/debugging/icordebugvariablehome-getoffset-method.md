---
title: 'Método ICorDebugVariableHome:: GetOffset'
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
ms.openlocfilehash: 3af8c925b80b9fd4ed0a46d2bd50fe37a6f3154a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125091"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="d9e88-102">Método ICorDebugVariableHome:: GetOffset</span><span class="sxs-lookup"><span data-stu-id="d9e88-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="d9e88-103">Obtém o deslocamento do registro base de uma variável.</span><span class="sxs-lookup"><span data-stu-id="d9e88-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e88-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9e88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9e88-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9e88-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="d9e88-106">fora O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="d9e88-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e88-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d9e88-107">Return Value</span></span>  
 <span data-ttu-id="d9e88-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d9e88-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="d9e88-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d9e88-109">Value</span></span>|<span data-ttu-id="d9e88-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9e88-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d9e88-111">A variável está em um local de memória relativa ao registro.</span><span class="sxs-lookup"><span data-stu-id="d9e88-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d9e88-112">A variável não está em um local de memória relativa ao registro.</span><span class="sxs-lookup"><span data-stu-id="d9e88-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9e88-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9e88-113">Requirements</span></span>  
 <span data-ttu-id="d9e88-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9e88-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e88-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9e88-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9e88-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9e88-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9e88-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e88-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e88-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9e88-118">See also</span></span>

- [<span data-ttu-id="d9e88-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d9e88-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
