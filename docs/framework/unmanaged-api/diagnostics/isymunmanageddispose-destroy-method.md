---
title: Método ISymUnmanagedDispose::Destroy
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d4b5f94bdbb7319cef14c8b86f8ea995df7ff21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="a53f4-102">Método ISymUnmanagedDispose::Destroy</span><span class="sxs-lookup"><span data-stu-id="a53f4-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="a53f4-103">Faz com que o objeto subjacente liberar todas as referências internas e retornar falha em todas as chamadas método subsequentes.</span><span class="sxs-lookup"><span data-stu-id="a53f4-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a53f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a53f4-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a53f4-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a53f4-105">Return Value</span></span>  
 <span data-ttu-id="a53f4-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a53f4-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a53f4-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a53f4-107">Requirements</span></span>  
 <span data-ttu-id="a53f4-108">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a53f4-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53f4-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a53f4-109">See Also</span></span>  
 [<span data-ttu-id="a53f4-110">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="a53f4-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
