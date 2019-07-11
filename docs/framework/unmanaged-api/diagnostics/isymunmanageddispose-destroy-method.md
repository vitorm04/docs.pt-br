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
ms.openlocfilehash: 23228c1414f5f6327cfb326c95a3224ae231a033
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776777"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="506df-102">Método ISymUnmanagedDispose::Destroy</span><span class="sxs-lookup"><span data-stu-id="506df-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="506df-103">Faz com que o objeto subjacente liberar todas as referências internas e retornar a falha em todas as chamadas método subsequentes.</span><span class="sxs-lookup"><span data-stu-id="506df-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="506df-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="506df-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="506df-105">Return Value</span></span>  
 <span data-ttu-id="506df-106">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="506df-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="506df-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="506df-107">Requirements</span></span>  
 <span data-ttu-id="506df-108">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="506df-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506df-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="506df-109">See also</span></span>

- [<span data-ttu-id="506df-110">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="506df-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
