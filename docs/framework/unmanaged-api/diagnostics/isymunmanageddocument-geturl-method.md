---
title: Método ISymUnmanagedDocument::GetURL
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b42bb72975fad4c1830a961f83d9e3065d055b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187454"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="4037a-102">Método ISymUnmanagedDocument::GetURL</span><span class="sxs-lookup"><span data-stu-id="4037a-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="4037a-103">Retorna o localizador recursos uniforme (URL) para este documento.</span><span class="sxs-lookup"><span data-stu-id="4037a-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4037a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4037a-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4037a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4037a-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="4037a-106">[in] O tamanho, em caracteres, da `szURL` buffer.</span><span class="sxs-lookup"><span data-stu-id="4037a-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="4037a-107">[out] Um ponteiro para uma variável que recebe o tamanho da URL, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="4037a-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="4037a-108">[out] O buffer que contém a URL.</span><span class="sxs-lookup"><span data-stu-id="4037a-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4037a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4037a-109">Return Value</span></span>  
 <span data-ttu-id="4037a-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4037a-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4037a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4037a-111">See also</span></span>

- [<span data-ttu-id="4037a-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="4037a-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
