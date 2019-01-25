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
ms.openlocfilehash: a6f8c8b522aabfce3b83b6b624bd0ca9757448ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666014"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="c73af-102">Método ISymUnmanagedWriter::CloseMethod</span><span class="sxs-lookup"><span data-stu-id="c73af-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="c73af-103">Fecha o método atual.</span><span class="sxs-lookup"><span data-stu-id="c73af-103">Closes the current method.</span></span> <span data-ttu-id="c73af-104">Quando um método é fechado, nenhuma mais símbolos podem ser definidos dentro dele.</span><span class="sxs-lookup"><span data-stu-id="c73af-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c73af-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c73af-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c73af-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c73af-106">Return Value</span></span>  
 <span data-ttu-id="c73af-107">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c73af-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c73af-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c73af-108">Requirements</span></span>  
 <span data-ttu-id="c73af-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c73af-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c73af-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c73af-110">See also</span></span>
- [<span data-ttu-id="c73af-111">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="c73af-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="c73af-112">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="c73af-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
