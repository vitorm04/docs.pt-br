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
ms.openlocfilehash: 7a4ffc0c417ae839e5c97ffe6884bc3230a603b7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610100"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="b0eba-102">Método ISymUnmanagedWriter::CloseNamespace</span><span class="sxs-lookup"><span data-stu-id="b0eba-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="b0eba-103">Fecha o namespace aberto mais recentemente.</span><span class="sxs-lookup"><span data-stu-id="b0eba-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0eba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0eba-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b0eba-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b0eba-105">Return Value</span></span>  
 <span data-ttu-id="b0eba-106">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b0eba-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0eba-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0eba-107">Requirements</span></span>  
 <span data-ttu-id="b0eba-108">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b0eba-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0eba-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0eba-109">See also</span></span>

- [<span data-ttu-id="b0eba-110">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="b0eba-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="b0eba-111">Método OpenNamespace</span><span class="sxs-lookup"><span data-stu-id="b0eba-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
