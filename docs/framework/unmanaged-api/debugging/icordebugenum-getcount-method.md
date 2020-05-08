---
title: Método ICorDebugEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::GetCount
helpviewer_keywords:
- ICorDebugEnum::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: d8a74304-1cb2-4977-a21d-e1af48c563ff
topic_type:
- apiref
ms.openlocfilehash: 90ba690897abced2d4f6282eedef91712d8ceeca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976337"
---
# <a name="icordebugenumgetcount-method"></a><span data-ttu-id="fd8c4-102">Método ICorDebugEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="fd8c4-102">ICorDebugEnum::GetCount Method</span></span>
<span data-ttu-id="fd8c4-103">Obtém o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd8c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd8c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd8c4-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="fd8c4-106">fora Um ponteiro para o número de itens na enumeração.</span><span class="sxs-lookup"><span data-stu-id="fd8c4-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8c4-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd8c4-107">Requirements</span></span>  
 <span data-ttu-id="fd8c4-108">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd8c4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8c4-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd8c4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd8c4-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd8c4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd8c4-111">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8c4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
