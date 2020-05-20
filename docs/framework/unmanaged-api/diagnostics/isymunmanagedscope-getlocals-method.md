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
ms.openlocfilehash: 0acd31d85504688427cace0222a657885035c537
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615378"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="2b321-102">Método ISymUnmanagedScope::GetLocals</span><span class="sxs-lookup"><span data-stu-id="2b321-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="2b321-103">Obtém as variáveis locais definidas nesse escopo.</span><span class="sxs-lookup"><span data-stu-id="2b321-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b321-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b321-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b321-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b321-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="2b321-106">no Um `ULONG32` que indica o tamanho da `locals` matriz.</span><span class="sxs-lookup"><span data-stu-id="2b321-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="2b321-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="2b321-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="2b321-108">fora A matriz que recebe as variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="2b321-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b321-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2b321-109">Return Value</span></span>  
 <span data-ttu-id="2b321-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2b321-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b321-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b321-111">Requirements</span></span>  
 <span data-ttu-id="2b321-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2b321-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b321-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="2b321-113">See also</span></span>

- [<span data-ttu-id="2b321-114">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="2b321-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
