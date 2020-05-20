---
title: Método ISymUnmanagedWriter::CloseMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: fdf24bb8533da7914128f9477987c427442383bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610113"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="d047c-102">Método ISymUnmanagedWriter::CloseMethod</span><span class="sxs-lookup"><span data-stu-id="d047c-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="d047c-103">Fecha o método atual.</span><span class="sxs-lookup"><span data-stu-id="d047c-103">Closes the current method.</span></span> <span data-ttu-id="d047c-104">Depois que um método é fechado, nenhum símbolo pode ser definido dentro dele.</span><span class="sxs-lookup"><span data-stu-id="d047c-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d047c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d047c-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d047c-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d047c-106">Return Value</span></span>  
 <span data-ttu-id="d047c-107">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d047c-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d047c-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d047c-108">Requirements</span></span>  
 <span data-ttu-id="d047c-109">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d047c-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d047c-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="d047c-110">See also</span></span>

- [<span data-ttu-id="d047c-111">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="d047c-111">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d047c-112">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="d047c-112">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)
