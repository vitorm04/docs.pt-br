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
ms.openlocfilehash: 5d8bc90cc07c2390cc83860b8009a3705f927e80
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776669"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="c809b-102">Método ISymUnmanagedDocument::GetURL</span><span class="sxs-lookup"><span data-stu-id="c809b-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="c809b-103">Retorna o localizador recursos uniforme (URL) para este documento.</span><span class="sxs-lookup"><span data-stu-id="c809b-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c809b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c809b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c809b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c809b-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="c809b-106">[in] O tamanho, em caracteres, da `szURL` buffer.</span><span class="sxs-lookup"><span data-stu-id="c809b-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="c809b-107">[out] Um ponteiro para uma variável que recebe o tamanho da URL, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="c809b-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="c809b-108">[out] O buffer que contém a URL.</span><span class="sxs-lookup"><span data-stu-id="c809b-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c809b-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c809b-109">Return Value</span></span>  
 <span data-ttu-id="c809b-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c809b-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c809b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c809b-111">See also</span></span>

- [<span data-ttu-id="c809b-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="c809b-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
