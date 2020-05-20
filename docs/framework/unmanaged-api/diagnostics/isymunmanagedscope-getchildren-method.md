---
title: Método ISymUnmanagedScope::GetChildren
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: c6d21f40c260890c9c88dcdfccd7e31161024ba3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614858"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="ce074-102">Método ISymUnmanagedScope::GetChildren</span><span class="sxs-lookup"><span data-stu-id="ce074-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="ce074-103">Obtém os filhos deste escopo.</span><span class="sxs-lookup"><span data-stu-id="ce074-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce074-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce074-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce074-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce074-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="ce074-106">no Um `ULONG32` que indica o tamanho da `children` matriz.</span><span class="sxs-lookup"><span data-stu-id="ce074-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="ce074-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os filhos.</span><span class="sxs-lookup"><span data-stu-id="ce074-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="ce074-108">fora A matriz de filhos retornada.</span><span class="sxs-lookup"><span data-stu-id="ce074-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce074-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ce074-109">Return Value</span></span>  
 <span data-ttu-id="ce074-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ce074-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce074-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce074-111">Requirements</span></span>  
 <span data-ttu-id="ce074-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ce074-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce074-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce074-113">See also</span></span>

- [<span data-ttu-id="ce074-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="ce074-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="ce074-115">Método GetParent</span><span class="sxs-lookup"><span data-stu-id="ce074-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
