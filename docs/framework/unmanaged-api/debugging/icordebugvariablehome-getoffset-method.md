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
ms.openlocfilehash: a6f93ec3c7ffe415c41dcf094dbde2f0a08969f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790996"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="a31b2-102">Método ICorDebugVariableHome:: GetOffset</span><span class="sxs-lookup"><span data-stu-id="a31b2-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="a31b2-103">Obtém o deslocamento do registro base de uma variável.</span><span class="sxs-lookup"><span data-stu-id="a31b2-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31b2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a31b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a31b2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a31b2-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="a31b2-106">fora O deslocamento do registro base.</span><span class="sxs-lookup"><span data-stu-id="a31b2-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a31b2-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a31b2-107">Return Value</span></span>  
 <span data-ttu-id="a31b2-108">O método retorna os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="a31b2-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="a31b2-109">Value</span><span class="sxs-lookup"><span data-stu-id="a31b2-109">Value</span></span>|<span data-ttu-id="a31b2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a31b2-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="a31b2-111">A variável está em um local de memória relativa ao registro.</span><span class="sxs-lookup"><span data-stu-id="a31b2-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="a31b2-112">A variável não está em um local de memória relativa ao registro.</span><span class="sxs-lookup"><span data-stu-id="a31b2-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a31b2-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a31b2-113">Requirements</span></span>  
 <span data-ttu-id="a31b2-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a31b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a31b2-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a31b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a31b2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a31b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a31b2-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a31b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31b2-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="a31b2-118">See also</span></span>

- [<span data-ttu-id="a31b2-119">Interface ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="a31b2-119">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
