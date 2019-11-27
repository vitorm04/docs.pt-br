---
title: Método ISymUnmanagedMethod::GetScopeFromOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 36b1b2394907f242c0e8c5e277c0d1c5b3b02e1b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448907"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="3555a-102">Método ISymUnmanagedMethod::GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="3555a-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="3555a-103">Obtém o escopo léxico mais delimitador dentro desse método que envolve o deslocamento fornecido.</span><span class="sxs-lookup"><span data-stu-id="3555a-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="3555a-104">Isso pode ser usado para iniciar pesquisas de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="3555a-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3555a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3555a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3555a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3555a-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="3555a-107">no Um `ULONG` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="3555a-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3555a-108">fora Um ponteiro que é definido para a interface [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="3555a-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3555a-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3555a-109">Return Value</span></span>  
 <span data-ttu-id="3555a-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3555a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3555a-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="3555a-111">Requirements</span></span>  
 <span data-ttu-id="3555a-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3555a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3555a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3555a-113">See also</span></span>

- [<span data-ttu-id="3555a-114">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="3555a-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
