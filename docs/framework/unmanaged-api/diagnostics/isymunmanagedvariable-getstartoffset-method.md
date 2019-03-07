---
title: Método ISymUnmanagedVariable::GetStartOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996f9af1bccb446ad4fcc6faec60b88e511262de
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474274"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="694ac-102">Método ISymUnmanagedVariable::GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="694ac-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="694ac-103">Obtém o deslocamento do início dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="694ac-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="694ac-104">Quando se trata de uma variável local dentro de um escopo, o deslocamento de início se enquadram dentro dos deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="694ac-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="694ac-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="694ac-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="694ac-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="694ac-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="694ac-107">[out] Um ponteiro para um `ULONG32` que recebe o deslocamento inicial.</span><span class="sxs-lookup"><span data-stu-id="694ac-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="694ac-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="694ac-108">Return Value</span></span>  
 <span data-ttu-id="694ac-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="694ac-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="694ac-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="694ac-110">Requirements</span></span>  
 <span data-ttu-id="694ac-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="694ac-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="694ac-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="694ac-112">See also</span></span>
- [<span data-ttu-id="694ac-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="694ac-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="694ac-114">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="694ac-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
