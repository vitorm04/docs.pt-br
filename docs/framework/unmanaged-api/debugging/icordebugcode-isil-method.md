---
title: Método ICorDebugCode::IsIL
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a81f4a53954c559ab12e27bcf039b7b1a1804cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700788"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="111d6-102">Método ICorDebugCode::IsIL</span><span class="sxs-lookup"><span data-stu-id="111d6-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="111d6-103">Obtém um valor que indica se este "ICorDebugCode" representa o código que foi compilado na MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="111d6-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="111d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="111d6-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="111d6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="111d6-105">Parameters</span></span>
 `pbIL`  
 <span data-ttu-id="111d6-106">[out] `true` se este `ICorDebugCode` representa o código que foi compilado em MSIL; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="111d6-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="111d6-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="111d6-107">Requirements</span></span>

 <span data-ttu-id="111d6-108">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="111d6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  

 <span data-ttu-id="111d6-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="111d6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  

 <span data-ttu-id="111d6-110">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="111d6-110">**Library:** CorGuids.lib</span></span>  

 <span data-ttu-id="111d6-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="111d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
 
