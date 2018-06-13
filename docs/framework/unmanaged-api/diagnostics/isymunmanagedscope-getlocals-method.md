---
title: Método ISymUnmanagedScope::GetLocals
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 781111db30ae664c9dd45744f88387e161f2716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426793"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="b9e3a-102">Método ISymUnmanagedScope::GetLocals</span><span class="sxs-lookup"><span data-stu-id="b9e3a-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="b9e3a-103">Obtém as variáveis locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="b9e3a-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9e3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9e3a-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9e3a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9e3a-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="b9e3a-106">[in] Um `ULONG32` que indica o tamanho do `locals` matriz.</span><span class="sxs-lookup"><span data-stu-id="b9e3a-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="b9e3a-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="b9e3a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="b9e3a-108">[out] A matriz que recebe as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="b9e3a-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9e3a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b9e3a-109">Return Value</span></span>  
 <span data-ttu-id="b9e3a-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b9e3a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9e3a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9e3a-111">Requirements</span></span>  
 <span data-ttu-id="b9e3a-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b9e3a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e3a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9e3a-113">See Also</span></span>  
 [<span data-ttu-id="b9e3a-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="b9e3a-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
