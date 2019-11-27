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
ms.openlocfilehash: 1fcb885b6e19457065c2ca9971f068b42f97147d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448349"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="cdb21-102">Método ISymUnmanagedReader::GetDocument</span><span class="sxs-lookup"><span data-stu-id="cdb21-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="cdb21-103">Localiza um documento.</span><span class="sxs-lookup"><span data-stu-id="cdb21-103">Finds a document.</span></span> <span data-ttu-id="cdb21-104">O idioma do documento, o fornecedor e o tipo são opcionais.</span><span class="sxs-lookup"><span data-stu-id="cdb21-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb21-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdb21-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdb21-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cdb21-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="cdb21-107">no A URL que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="cdb21-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="cdb21-108">no O idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="cdb21-108">[in] The document language.</span></span> <span data-ttu-id="cdb21-109">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="cdb21-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="cdb21-110">no A identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="cdb21-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="cdb21-111">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="cdb21-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="cdb21-112">no O tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="cdb21-112">[in] The type of the document.</span></span> <span data-ttu-id="cdb21-113">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="cdb21-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="cdb21-114">fora Um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="cdb21-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdb21-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cdb21-115">Return Value</span></span>  
 <span data-ttu-id="cdb21-116">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="cdb21-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb21-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="cdb21-117">Requirements</span></span>  
 <span data-ttu-id="cdb21-118">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cdb21-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb21-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdb21-119">See also</span></span>

- [<span data-ttu-id="cdb21-120">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="cdb21-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
