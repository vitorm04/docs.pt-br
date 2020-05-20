---
title: Método ISymUnmanagedDocument::GetLanguage
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: 084f3ae12d906f5e80fdb86e65b09d2371fd246b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614585"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="4aee0-102">Método ISymUnmanagedDocument::GetLanguage</span><span class="sxs-lookup"><span data-stu-id="4aee0-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="4aee0-103">Obtém o identificador de idioma deste documento</span><span class="sxs-lookup"><span data-stu-id="4aee0-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aee0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4aee0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4aee0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4aee0-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4aee0-106">fora Um ponteiro para uma variável que recebe o identificador de idioma.</span><span class="sxs-lookup"><span data-stu-id="4aee0-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4aee0-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4aee0-107">Return Value</span></span>  
 <span data-ttu-id="4aee0-108">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="4aee0-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aee0-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="4aee0-109">See also</span></span>

- [<span data-ttu-id="4aee0-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="4aee0-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
