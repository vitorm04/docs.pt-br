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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ce47953358b7025e30080fbbaf288a6c0e879d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939835"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="537cb-102">Método ISymUnmanagedDocument::GetLanguage</span><span class="sxs-lookup"><span data-stu-id="537cb-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="537cb-103">Obtém o identificador de idioma deste documento</span><span class="sxs-lookup"><span data-stu-id="537cb-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="537cb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="537cb-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="537cb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="537cb-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="537cb-106">[out] Um ponteiro para uma variável que recebe o identificador de idioma.</span><span class="sxs-lookup"><span data-stu-id="537cb-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="537cb-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="537cb-107">Return Value</span></span>  
 <span data-ttu-id="537cb-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="537cb-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="537cb-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="537cb-109">See also</span></span>

- [<span data-ttu-id="537cb-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="537cb-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
