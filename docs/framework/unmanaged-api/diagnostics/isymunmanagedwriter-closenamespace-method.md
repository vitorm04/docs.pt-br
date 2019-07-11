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
ms.openlocfilehash: 3ed618847d398bb4dcccb8ecebabdc947390c874
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778168"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="af30c-102">Método ISymUnmanagedWriter::CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="af30c-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="af30c-103">Fecha abriu mais recentemente namespace.</span><span class="sxs-lookup"><span data-stu-id="af30c-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af30c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af30c-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="af30c-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="af30c-105">Return Value</span></span>  
 <span data-ttu-id="af30c-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="af30c-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af30c-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af30c-107">Requirements</span></span>  
 <span data-ttu-id="af30c-108">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="af30c-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af30c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af30c-109">See also</span></span>

- [<span data-ttu-id="af30c-110">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="af30c-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="af30c-111">Método OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="af30c-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
