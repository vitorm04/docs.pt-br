---
title: "Método ISymUnmanagedDocument::GetURL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetURL
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 591383fee2f9b22a00956193555c719e72d722bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="d2610-102">Método ISymUnmanagedDocument::GetURL</span><span class="sxs-lookup"><span data-stu-id="d2610-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="d2610-103">Retorna o uniform resource locator (URL) para este documento.</span><span class="sxs-lookup"><span data-stu-id="d2610-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2610-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2610-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2610-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d2610-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="d2610-106">[in] O tamanho, em caracteres, do `szURL` buffer.</span><span class="sxs-lookup"><span data-stu-id="d2610-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="d2610-107">[out] Um ponteiro para uma variável que recebe o tamanho da URL, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="d2610-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="d2610-108">[out] O buffer que contém a URL.</span><span class="sxs-lookup"><span data-stu-id="d2610-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2610-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d2610-109">Return Value</span></span>  
 <span data-ttu-id="d2610-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="d2610-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2610-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2610-111">See Also</span></span>  
 [<span data-ttu-id="d2610-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="d2610-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
