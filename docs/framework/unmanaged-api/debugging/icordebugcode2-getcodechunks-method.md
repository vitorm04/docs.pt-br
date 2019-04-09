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
ms.openlocfilehash: 1428fc245d4f6993050c2753321684afee488c0e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116775"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="c4684-102">Método ICorDebugCode2::GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="c4684-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="c4684-103">Obtém as partes do código que é composto por este objeto de código.</span><span class="sxs-lookup"><span data-stu-id="c4684-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4684-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4684-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4684-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4684-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="c4684-106">[in] Tamanho do `chunks` matriz.</span><span class="sxs-lookup"><span data-stu-id="c4684-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="c4684-107">[out] O número de partes retornado no `chunks` matriz.</span><span class="sxs-lookup"><span data-stu-id="c4684-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="c4684-108">[out] Uma matriz de estruturas de "CodeChunkInfo", cada um deles representa um único bloco de código.</span><span class="sxs-lookup"><span data-stu-id="c4684-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="c4684-109">Se o valor de `cbufSize` for 0, esse parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="c4684-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4684-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4684-110">Remarks</span></span>  
 <span data-ttu-id="c4684-111">As partes de código nunca serão sobrepostas, e eles seguirão a ordem em que eles seriam tenham sido concatenados por [icordebugcode:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="c4684-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="c4684-112">Um objeto de código Microsoft intermediate language (MSIL) no .NET Framework versão 2.0 compõem uma parte de código único.</span><span class="sxs-lookup"><span data-stu-id="c4684-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4684-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4684-113">Requirements</span></span>  
 <span data-ttu-id="c4684-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4684-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4684-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4684-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4684-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4684-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c4684-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c4684-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c4684-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4684-118">See also</span></span>
