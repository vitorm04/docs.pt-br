---
title: "Método ISymUnmanagedVariable::GetEndOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f91c2b0f4ecb4cc901a0389d15f4d69e926cf8f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="6481f-102">Método ISymUnmanagedVariable::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="6481f-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="6481f-103">Obtém o deslocamento de fim desta variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="6481f-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="6481f-104">Se esta é uma variável local dentro de um escopo, se o deslocamento de fim dentro os deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="6481f-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6481f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6481f-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6481f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6481f-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6481f-107">[out] Um ponteiro para um `ULONG32` que recebe o deslocamento de fim.</span><span class="sxs-lookup"><span data-stu-id="6481f-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6481f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6481f-108">Return Value</span></span>  
 <span data-ttu-id="6481f-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6481f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6481f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6481f-110">Requirements</span></span>  
 <span data-ttu-id="6481f-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6481f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6481f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6481f-112">See Also</span></span>  
 [<span data-ttu-id="6481f-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="6481f-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="6481f-114">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="6481f-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
