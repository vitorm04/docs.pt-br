---
title: Método ISymUnmanagedWriter::CloseNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f8804c911e053758442670afb3c3f27d0f7453
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130046"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="41888-102">Método ISymUnmanagedWriter::CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="41888-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="41888-103">Fecha abriu mais recentemente namespace.</span><span class="sxs-lookup"><span data-stu-id="41888-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41888-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41888-104">Syntax</span></span>  
  
```  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="41888-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="41888-105">Return Value</span></span>  
 <span data-ttu-id="41888-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="41888-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41888-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41888-107">Requirements</span></span>  
 <span data-ttu-id="41888-108">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="41888-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41888-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41888-109">See also</span></span>

- [<span data-ttu-id="41888-110">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="41888-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="41888-111">Método OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="41888-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
