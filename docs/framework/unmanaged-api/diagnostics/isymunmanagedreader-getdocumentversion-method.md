---
title: Método ISymUnmanagedReader::GetDocumentVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf6a08b17819e3d3cdaa62b0e209fc2064de4a4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688695"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="a1dbc-102">Método ISymUnmanagedReader::GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="a1dbc-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="a1dbc-103">Obtém a versão especificada do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="a1dbc-104">A versão do documento começa em 1 e é incrementada toda vez que o documento é atualizado usando o [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="a1dbc-105">Se o `pbCurrent` parâmetro é `true`, essa é a versão mais recente do documento.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1dbc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1dbc-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1dbc-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1dbc-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="a1dbc-108">[in] O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="a1dbc-109">[out] Um ponteiro para uma variável que recebe a versão do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="a1dbc-110">[out] Um ponteiro para uma variável que recebe `true` se esta for a versão mais recente do documento, ou `false` se não for a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1dbc-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a1dbc-111">Return Value</span></span>  
 <span data-ttu-id="a1dbc-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a1dbc-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1dbc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1dbc-113">Requirements</span></span>  
 <span data-ttu-id="a1dbc-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a1dbc-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1dbc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1dbc-115">See also</span></span>
- [<span data-ttu-id="a1dbc-116">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="a1dbc-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
