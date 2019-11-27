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
ms.openlocfilehash: e930a9a3753ccf2b8aff798916c876fbedad4df4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430706"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="4b067-102">Método ISymUnmanagedDispose::Destroy</span><span class="sxs-lookup"><span data-stu-id="4b067-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="4b067-103">Faz com que o objeto subjacente libere todas as referências internas e retorne a falha em qualquer chamada de método subsequente.</span><span class="sxs-lookup"><span data-stu-id="4b067-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b067-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b067-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4b067-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4b067-105">Return Value</span></span>  
 <span data-ttu-id="4b067-106">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4b067-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b067-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b067-107">Requirements</span></span>  
 <span data-ttu-id="4b067-108">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4b067-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b067-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b067-109">See also</span></span>

- [<span data-ttu-id="4b067-110">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="4b067-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
