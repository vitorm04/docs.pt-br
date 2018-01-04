---
title: "Método ISymENCUnmanagedMethod::GetLineFromOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535c0310a3220c5691f26c9081f6d2f747196e91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="f80c8-102">Método ISymENCUnmanagedMethod::GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="f80c8-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="f80c8-103">Obtém as informações de linha associadas com um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="f80c8-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="f80c8-104">Se o parâmetro de deslocamento (`dwOffset`) não é um ponto de sequência, esse método obtém as informações de linha associadas com o deslocamento anterior.</span><span class="sxs-lookup"><span data-stu-id="f80c8-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f80c8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f80c8-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f80c8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f80c8-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="f80c8-107">[in] Um `ULONG32` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="f80c8-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="f80c8-108">[out] Um ponteiro para um `ULONG32` que recebe a linha.</span><span class="sxs-lookup"><span data-stu-id="f80c8-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="f80c8-109">[out] Um ponteiro para um `ULONG32` que recebe a coluna.</span><span class="sxs-lookup"><span data-stu-id="f80c8-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="f80c8-110">[out] Um ponteiro para um `ULONG32` que recebe a fim de linha.</span><span class="sxs-lookup"><span data-stu-id="f80c8-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="f80c8-111">[out] Um ponteiro para um `ULONG32` que recebe a coluna final.</span><span class="sxs-lookup"><span data-stu-id="f80c8-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="f80c8-112">[out] Um ponteiro para um `ULONG32` que recebe o ponto de sequência associado.</span><span class="sxs-lookup"><span data-stu-id="f80c8-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f80c8-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f80c8-113">Return Value</span></span>  
 <span data-ttu-id="f80c8-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f80c8-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f80c8-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f80c8-115">Requirements</span></span>  
 <span data-ttu-id="f80c8-116">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f80c8-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f80c8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f80c8-117">See Also</span></span>  
 [<span data-ttu-id="f80c8-118">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="f80c8-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
