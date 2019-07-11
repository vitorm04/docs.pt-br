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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23f77f30b84622dffd8c76bb9302ad564f40ed41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778183"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="f1ced-102">Método ISymUnmanagedWriter::CloseMethod</span><span class="sxs-lookup"><span data-stu-id="f1ced-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="f1ced-103">Fecha o método atual.</span><span class="sxs-lookup"><span data-stu-id="f1ced-103">Closes the current method.</span></span> <span data-ttu-id="f1ced-104">Quando um método é fechado, nenhuma mais símbolos podem ser definidos dentro dele.</span><span class="sxs-lookup"><span data-stu-id="f1ced-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ced-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1ced-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f1ced-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1ced-106">Return Value</span></span>  
 <span data-ttu-id="f1ced-107">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f1ced-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1ced-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1ced-108">Requirements</span></span>  
 <span data-ttu-id="f1ced-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f1ced-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ced-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1ced-110">See also</span></span>

- [<span data-ttu-id="f1ced-111">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="f1ced-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="f1ced-112">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="f1ced-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
