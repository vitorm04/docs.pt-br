---
title: Método ISymUnmanagedReader::GetDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 950fb3b9c51ae2c9470b5aadd31c877d7aa6b6f6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615053"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="06545-102">Método ISymUnmanagedReader::GetDocument</span><span class="sxs-lookup"><span data-stu-id="06545-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="06545-103">Localiza um documento.</span><span class="sxs-lookup"><span data-stu-id="06545-103">Finds a document.</span></span> <span data-ttu-id="06545-104">O idioma do documento, o fornecedor e o tipo são opcionais.</span><span class="sxs-lookup"><span data-stu-id="06545-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06545-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06545-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06545-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06545-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="06545-107">no A URL que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="06545-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="06545-108">no O idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="06545-108">[in] The document language.</span></span> <span data-ttu-id="06545-109">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="06545-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="06545-110">no A identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="06545-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="06545-111">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="06545-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="06545-112">no O tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="06545-112">[in] The type of the document.</span></span> <span data-ttu-id="06545-113">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="06545-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="06545-114">fora Um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="06545-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06545-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="06545-115">Return Value</span></span>  
 <span data-ttu-id="06545-116">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="06545-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06545-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06545-117">Requirements</span></span>  
 <span data-ttu-id="06545-118">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="06545-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06545-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="06545-119">See also</span></span>

- [<span data-ttu-id="06545-120">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="06545-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
