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
ms.openlocfilehash: 3685707f1983ffec413e9cea2df5034ac53f643a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615586"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="9554d-102">Método ISymUnmanagedDocument::GetURL</span><span class="sxs-lookup"><span data-stu-id="9554d-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="9554d-103">Retorna o Uniform Resource Locator (URL) deste documento.</span><span class="sxs-lookup"><span data-stu-id="9554d-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9554d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9554d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9554d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9554d-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="9554d-106">no O tamanho, em caracteres, do `szURL` buffer.</span><span class="sxs-lookup"><span data-stu-id="9554d-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="9554d-107">fora Um ponteiro para uma variável que recebe o tamanho da URL, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="9554d-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="9554d-108">fora O buffer que contém a URL.</span><span class="sxs-lookup"><span data-stu-id="9554d-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9554d-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9554d-109">Return Value</span></span>  
 <span data-ttu-id="9554d-110">S_OK se o método tiver sucesso; caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="9554d-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9554d-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="9554d-111">See also</span></span>

- [<span data-ttu-id="9554d-112">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="9554d-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
