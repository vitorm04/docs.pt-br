---
title: Método ISymENCUnmanagedMethod::GetLineFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3106c6680750826306cffb31e599ee2260bf4ad7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136442"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="b441d-102">Método ISymENCUnmanagedMethod::GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="b441d-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="b441d-103">Obtém as informações de linha associadas com um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="b441d-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="b441d-104">Se o parâmetro offset (`dwOffset`) não é um ponto de sequência, esse método obtém as informações de linha associadas com a diferença anterior.</span><span class="sxs-lookup"><span data-stu-id="b441d-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b441d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b441d-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b441d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b441d-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="b441d-107">[in] Um `ULONG32` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="b441d-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="b441d-108">[out] Um ponteiro para um `ULONG32` que recebe a linha.</span><span class="sxs-lookup"><span data-stu-id="b441d-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="b441d-109">[out] Um ponteiro para um `ULONG32` que recebe a coluna.</span><span class="sxs-lookup"><span data-stu-id="b441d-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="b441d-110">[out] Um ponteiro para um `ULONG32` que recebe a linha final.</span><span class="sxs-lookup"><span data-stu-id="b441d-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="b441d-111">[out] Um ponteiro para um `ULONG32` que recebe a coluna final.</span><span class="sxs-lookup"><span data-stu-id="b441d-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="b441d-112">[out] Um ponteiro para um `ULONG32` que recebe o ponto de sequência associado.</span><span class="sxs-lookup"><span data-stu-id="b441d-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b441d-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b441d-113">Return Value</span></span>  
 <span data-ttu-id="b441d-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b441d-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b441d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b441d-115">Requirements</span></span>  
 <span data-ttu-id="b441d-116">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b441d-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b441d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b441d-117">See also</span></span>

- [<span data-ttu-id="b441d-118">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="b441d-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
