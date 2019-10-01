---
title: Método ICorDebugCode::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89df0e9be0600b51dcc8a68c5aba3f06e86e1b53
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700812"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="cef23-102">Método ICorDebugCode::GetSize</span><span class="sxs-lookup"><span data-stu-id="cef23-102">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="cef23-103">Obtém o tamanho, em bytes, do código binário representado por este "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="cef23-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="cef23-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cef23-104">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="cef23-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cef23-105">Parameters</span></span>

 `pcBytes`  
 <span data-ttu-id="cef23-106">fora Um ponteiro para o tamanho, em bytes, do código binário que esse objeto `ICorDebugCode` representa.</span><span class="sxs-lookup"><span data-stu-id="cef23-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="cef23-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cef23-107">Requirements</span></span>

 <span data-ttu-id="cef23-108">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cef23-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="cef23-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cef23-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="cef23-110">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cef23-110">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="cef23-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cef23-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
 
