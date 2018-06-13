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
ms.openlocfilehash: 0898d554a2602a1139f2e37eb67f3aa00c5bd79e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436079"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="ff529-102">Método ISymUnmanagedMethod::GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="ff529-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="ff529-103">Obtém o escopo léxico mais delimitador dentro desse método que inclui o deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="ff529-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="ff529-104">Isso pode ser usado para iniciar a pesquisa de variável local.</span><span class="sxs-lookup"><span data-stu-id="ff529-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff529-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff529-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff529-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff529-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="ff529-107">[in] Um `ULONG` que contém o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="ff529-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ff529-108">[out] Um ponteiro que está definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="ff529-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff529-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ff529-109">Return Value</span></span>  
 <span data-ttu-id="ff529-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ff529-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff529-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff529-111">Requirements</span></span>  
 <span data-ttu-id="ff529-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ff529-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff529-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff529-113">See Also</span></span>  
 [<span data-ttu-id="ff529-114">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="ff529-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
