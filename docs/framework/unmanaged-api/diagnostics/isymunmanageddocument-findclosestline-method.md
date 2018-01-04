---
title: "Método ISymUnmanagedDocument::FindClosestLine"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.FindClosestLine
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5467f7d500719e8849b85a57195e98c6eeb7fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="b14c8-102">Método ISymUnmanagedDocument::FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="b14c8-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="b14c8-103">Retorna a linha mais próxima que seja um ponto de sequência, de acordo com uma linha neste documento que pode ou não ser um ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="b14c8-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b14c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b14c8-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b14c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b14c8-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="b14c8-106">[in] Uma linha neste documento.</span><span class="sxs-lookup"><span data-stu-id="b14c8-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b14c8-107">[out] Um ponteiro para uma variável que recebe a linha.</span><span class="sxs-lookup"><span data-stu-id="b14c8-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b14c8-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b14c8-108">Return Value</span></span>  
 <span data-ttu-id="b14c8-109">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b14c8-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14c8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b14c8-110">See Also</span></span>  
 [<span data-ttu-id="b14c8-111">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="b14c8-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
