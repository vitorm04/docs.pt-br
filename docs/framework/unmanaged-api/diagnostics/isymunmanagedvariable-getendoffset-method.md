---
title: Método ISymUnmanagedVariable::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ef32a963b73f2109b9747ef303e8ccd6a729838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778265"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="80349-102">Método ISymUnmanagedVariable::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="80349-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="80349-103">Obtém o deslocamento final dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="80349-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="80349-104">Quando se trata de uma variável local dentro de um escopo, o deslocamento final se enquadram dentro dos deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="80349-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80349-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80349-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80349-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80349-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="80349-107">[out] Um ponteiro para um `ULONG32` que recebe o deslocamento de fim.</span><span class="sxs-lookup"><span data-stu-id="80349-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80349-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="80349-108">Return Value</span></span>  
 <span data-ttu-id="80349-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="80349-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80349-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80349-110">Requirements</span></span>  
 <span data-ttu-id="80349-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="80349-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80349-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80349-112">See also</span></span>

- [<span data-ttu-id="80349-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="80349-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="80349-114">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="80349-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
