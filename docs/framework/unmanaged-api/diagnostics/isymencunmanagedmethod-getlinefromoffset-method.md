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
ms.openlocfilehash: 94a571a4bc01b805387aebe5a6e23bad0b735313
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448645"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="9190a-102">Método ISymENCUnmanagedMethod::GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="9190a-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="9190a-103">Obtém as informações de linha associadas a um deslocamento.</span><span class="sxs-lookup"><span data-stu-id="9190a-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="9190a-104">Se o parâmetro offset (`dwOffset`) não for um ponto de sequência, esse método obterá as informações de linha associadas ao deslocamento anterior.</span><span class="sxs-lookup"><span data-stu-id="9190a-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9190a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9190a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9190a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9190a-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="9190a-107">no Um `ULONG32` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="9190a-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="9190a-108">fora Um ponteiro para um `ULONG32` que recebe a linha.</span><span class="sxs-lookup"><span data-stu-id="9190a-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="9190a-109">fora Um ponteiro para um `ULONG32` que recebe a coluna.</span><span class="sxs-lookup"><span data-stu-id="9190a-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="9190a-110">fora Um ponteiro para um `ULONG32` que recebe a linha final.</span><span class="sxs-lookup"><span data-stu-id="9190a-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="9190a-111">fora Um ponteiro para um `ULONG32` que recebe a coluna final.</span><span class="sxs-lookup"><span data-stu-id="9190a-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="9190a-112">fora Um ponteiro para um `ULONG32` que recebe o ponto de sequência associado.</span><span class="sxs-lookup"><span data-stu-id="9190a-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9190a-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9190a-113">Return Value</span></span>  
 <span data-ttu-id="9190a-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9190a-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9190a-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9190a-115">Requirements</span></span>  
 <span data-ttu-id="9190a-116">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9190a-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9190a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9190a-117">See also</span></span>

- [<span data-ttu-id="9190a-118">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="9190a-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
