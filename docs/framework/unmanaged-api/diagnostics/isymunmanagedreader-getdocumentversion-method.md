---
title: "Método ISymUnmanagedReader::GetDocumentVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocumentVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2cb0abf887abaac4d7433b52a795beca509ec61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="845e5-102">Método ISymUnmanagedReader::GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="845e5-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="845e5-103">Obtém a versão especificada do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="845e5-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="845e5-104">A versão do documento começa em 1 e é incrementada toda vez que o documento é atualizado usando o [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="845e5-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="845e5-105">Se o `pbCurrent` parâmetro é `true`, esta é a versão mais recente do documento.</span><span class="sxs-lookup"><span data-stu-id="845e5-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="845e5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="845e5-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="845e5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="845e5-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="845e5-108">[in] O documento especificado.</span><span class="sxs-lookup"><span data-stu-id="845e5-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="845e5-109">[out] Um ponteiro para uma variável que recebe a versão do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="845e5-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="845e5-110">[out] Um ponteiro para uma variável que recebe `true` se esta é a versão mais recente do documento, ou `false` se não for a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="845e5-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="845e5-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="845e5-111">Return Value</span></span>  
 <span data-ttu-id="845e5-112">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="845e5-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="845e5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="845e5-113">Requirements</span></span>  
 <span data-ttu-id="845e5-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="845e5-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845e5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="845e5-115">See Also</span></span>  
 [<span data-ttu-id="845e5-116">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="845e5-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
