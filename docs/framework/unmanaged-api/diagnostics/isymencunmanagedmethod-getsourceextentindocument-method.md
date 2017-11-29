---
title: "Método ISymENCUnmanagedMethod::GetSourceExtentInDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cff81968926f608de8d28d730a00e79dc8b1c3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="a1985-102">Método ISymENCUnmanagedMethod::GetSourceExtentInDocument</span><span class="sxs-lookup"><span data-stu-id="a1985-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="a1985-103">Obtém o menor início linha e maior final para o método em um documento específico.</span><span class="sxs-lookup"><span data-stu-id="a1985-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1985-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1985-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1985-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1985-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a1985-106">[in] Um ponteiro para o documento.</span><span class="sxs-lookup"><span data-stu-id="a1985-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="a1985-107">[out] Um ponteiro para um `ULONG32` que recebe a primeira linha.</span><span class="sxs-lookup"><span data-stu-id="a1985-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="a1985-108">[out] Um ponteiro para um `ULONG32` que recebe a fim de linha.</span><span class="sxs-lookup"><span data-stu-id="a1985-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1985-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a1985-109">Return Value</span></span>  
 <span data-ttu-id="a1985-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a1985-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1985-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1985-111">Requirements</span></span>  
 <span data-ttu-id="a1985-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a1985-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1985-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1985-113">See Also</span></span>  
 [<span data-ttu-id="a1985-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="a1985-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
