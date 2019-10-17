---
title: Método ICorDebugCode2::GetCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebed8ea1d4943007f8f18b0baa1c676a78207c2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395502"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="e0708-102">Método ICorDebugCode2::GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="e0708-102">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="e0708-103">Obtém os sinalizadores que especificam as condições sob as quais esse objeto de código era JIT (just-in-time) compilado ou gerado usando o gerador de imagem nativa (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="e0708-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="e0708-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0708-104">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="e0708-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0708-105">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="e0708-106">fora Um ponteiro para um valor da enumeração [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) que especifica o comportamento do compilador JIT ou do gerador de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="e0708-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0708-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0708-107">Requirements</span></span>

<span data-ttu-id="e0708-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0708-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e0708-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0708-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="e0708-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0708-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e0708-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0708-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
