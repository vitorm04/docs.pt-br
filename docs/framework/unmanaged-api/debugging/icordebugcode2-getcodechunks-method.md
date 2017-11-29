---
title: "Método ICorDebugCode2::GetCodeChunks"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCodeChunks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 950fd5c19e8827a63dcf075c42d3e0c18ff91261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="f1a19-102">Método ICorDebugCode2::GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="f1a19-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="f1a19-103">Obtém as partes do código que é composto por esse objeto de código.</span><span class="sxs-lookup"><span data-stu-id="f1a19-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1a19-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1a19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1a19-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="f1a19-106">[in] Tamanho do `chunks` matriz.</span><span class="sxs-lookup"><span data-stu-id="f1a19-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="f1a19-107">[out] O número de partes retornado no `chunks` matriz.</span><span class="sxs-lookup"><span data-stu-id="f1a19-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="f1a19-108">[out] Uma matriz de estruturas de "CodeChunkInfo", cada uma representando um único bloco de código.</span><span class="sxs-lookup"><span data-stu-id="f1a19-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="f1a19-109">Se o valor de `cbufSize` for 0, esse parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="f1a19-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1a19-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1a19-110">Remarks</span></span>  
 <span data-ttu-id="f1a19-111">Os blocos de código nunca serão sobrepostos e eles seguirão a ordem na qual eles seriam tenham sido concatenados por [: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="f1a19-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="f1a19-112">Um objeto de código Microsoft intermediate language (MSIL) no .NET Framework versão 2.0 compõem um bloco de código único.</span><span class="sxs-lookup"><span data-stu-id="f1a19-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1a19-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1a19-113">Requirements</span></span>  
 <span data-ttu-id="f1a19-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a19-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1a19-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a19-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a19-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a19-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a19-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1a19-118">See Also</span></span>  
 
