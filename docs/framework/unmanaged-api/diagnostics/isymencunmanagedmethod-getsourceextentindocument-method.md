---
title: Método ISymENCUnmanagedMethod::GetSourceExtentInDocument
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4948a853434b14845983addb0e6fa4012279084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776878"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="fc493-102">Método ISymENCUnmanagedMethod::GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="fc493-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="fc493-103">Obtém o menor início maior final de linha para o método e de linha em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="fc493-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc493-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc493-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc493-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fc493-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="fc493-106">[in] Um ponteiro para o documento.</span><span class="sxs-lookup"><span data-stu-id="fc493-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="fc493-107">[out] Um ponteiro para um `ULONG32` que recebe a linha inicial.</span><span class="sxs-lookup"><span data-stu-id="fc493-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="fc493-108">[out] Um ponteiro para um `ULONG32` que recebe a linha final.</span><span class="sxs-lookup"><span data-stu-id="fc493-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc493-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fc493-109">Return Value</span></span>  
 <span data-ttu-id="fc493-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="fc493-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc493-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc493-111">Requirements</span></span>  
 <span data-ttu-id="fc493-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc493-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc493-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc493-113">See also</span></span>

- [<span data-ttu-id="fc493-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="fc493-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
