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
ms.openlocfilehash: bf932b63973f93c56883f099ddaadd9d1519f337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446335"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="9feb5-102">Método ISymUnmanagedScope::GetLocals</span><span class="sxs-lookup"><span data-stu-id="9feb5-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="9feb5-103">Obtém as variáveis locais definidas nesse escopo.</span><span class="sxs-lookup"><span data-stu-id="9feb5-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9feb5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9feb5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9feb5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9feb5-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="9feb5-106">no Um `ULONG32` que indica o tamanho da matriz de `locals`.</span><span class="sxs-lookup"><span data-stu-id="9feb5-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="9feb5-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="9feb5-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="9feb5-108">fora A matriz que recebe as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="9feb5-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9feb5-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9feb5-109">Return Value</span></span>  
 <span data-ttu-id="9feb5-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9feb5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9feb5-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="9feb5-111">Requirements</span></span>  
 <span data-ttu-id="9feb5-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9feb5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9feb5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9feb5-113">See also</span></span>

- [<span data-ttu-id="9feb5-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="9feb5-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
