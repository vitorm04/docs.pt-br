---
title: Método ICorDebugCode2::GetCodeChunks
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d64773aa0d35f2e97232576d145dfcba624812ec
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395524"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="a898d-102">Método ICorDebugCode2::GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="a898d-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="a898d-103">Obtém as partes de código das quais este objeto de código é composto.</span><span class="sxs-lookup"><span data-stu-id="a898d-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="a898d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a898d-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="a898d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a898d-105">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="a898d-106">no Tamanho da matriz `chunks`.</span><span class="sxs-lookup"><span data-stu-id="a898d-106">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="a898d-107">fora O número de partes retornadas na matriz `chunks`.</span><span class="sxs-lookup"><span data-stu-id="a898d-107">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="a898d-108">fora Uma matriz de estruturas "CodeChunkInfo", cada uma representando uma única parte do código.</span><span class="sxs-lookup"><span data-stu-id="a898d-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="a898d-109">Se o valor de `cbufSize` for 0, esse parâmetro poderá ser nulo.</span><span class="sxs-lookup"><span data-stu-id="a898d-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="a898d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a898d-110">Remarks</span></span>

<span data-ttu-id="a898d-111">Os trechos de código nunca serão sobrepostos e eles seguirão a ordem em que seriam concatenados por [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="a898d-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="a898d-112">Um objeto de código MSIL (Microsoft Intermediate Language) no .NET Framework versão 2,0 incluirá uma única parte de código.</span><span class="sxs-lookup"><span data-stu-id="a898d-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="a898d-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a898d-113">Requirements</span></span>

<span data-ttu-id="a898d-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a898d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a898d-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a898d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a898d-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a898d-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a898d-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a898d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
