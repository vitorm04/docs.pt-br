---
title: "Método ISymUnmanagedVariable::GetStartOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b7fd3a64202224ef5a7cc348ee8e9974a664d09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="b5c57-102">Método ISymUnmanagedVariable::GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="b5c57-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="b5c57-103">Obtém o deslocamento do início dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="b5c57-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="b5c57-104">Se esta é uma variável local dentro de um escopo, se o deslocamento de início dentro os deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="b5c57-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c57-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5c57-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5c57-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5c57-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b5c57-107">[out] Um ponteiro para um `ULONG32` que recebe o deslocamento de início.</span><span class="sxs-lookup"><span data-stu-id="b5c57-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5c57-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b5c57-108">Return Value</span></span>  
 <span data-ttu-id="b5c57-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b5c57-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c57-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5c57-110">Requirements</span></span>  
 <span data-ttu-id="b5c57-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b5c57-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c57-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5c57-112">See Also</span></span>  
 [<span data-ttu-id="b5c57-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="b5c57-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="b5c57-114">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="b5c57-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
