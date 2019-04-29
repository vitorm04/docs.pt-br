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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0e859ba8b6ec247073b0b69b035ea4cf074ab05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939614"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="79cb1-102">Método ISymUnmanagedMethod::GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="79cb1-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="79cb1-103">Obtém o escopo léxico mais delimitador dentro desse método que inclui o deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="79cb1-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="79cb1-104">Isso pode ser usado para iniciar a pesquisa de variável local.</span><span class="sxs-lookup"><span data-stu-id="79cb1-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cb1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79cb1-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79cb1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="79cb1-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="79cb1-107">[in] Um `ULONG` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="79cb1-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="79cb1-108">[out] Um ponteiro que é definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="79cb1-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79cb1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="79cb1-109">Return Value</span></span>  
 <span data-ttu-id="79cb1-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="79cb1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79cb1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="79cb1-111">Requirements</span></span>  
 <span data-ttu-id="79cb1-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="79cb1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cb1-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79cb1-113">See also</span></span>

- [<span data-ttu-id="79cb1-114">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="79cb1-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
