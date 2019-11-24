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
ms.openlocfilehash: b8e72745eff09c6707afe5a5f20a1ddf38b239ae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448617"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="3975e-102">Método ISymENCUnmanagedMethod::GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="3975e-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="3975e-103">Obtém a menor linha inicial e a linha final maior para o método em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="3975e-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3975e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3975e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3975e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3975e-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="3975e-106">no Um ponteiro para o documento.</span><span class="sxs-lookup"><span data-stu-id="3975e-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="3975e-107">fora Um ponteiro para um `ULONG32` que recebe a linha inicial.</span><span class="sxs-lookup"><span data-stu-id="3975e-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="3975e-108">fora Um ponteiro para um `ULONG32` que recebe a linha final.</span><span class="sxs-lookup"><span data-stu-id="3975e-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3975e-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3975e-109">Return Value</span></span>  
 <span data-ttu-id="3975e-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3975e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3975e-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3975e-111">Requirements</span></span>  
 <span data-ttu-id="3975e-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3975e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3975e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3975e-113">See also</span></span>

- [<span data-ttu-id="3975e-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="3975e-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
