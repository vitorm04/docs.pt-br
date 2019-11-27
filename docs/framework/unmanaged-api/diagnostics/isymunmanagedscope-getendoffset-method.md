---
title: Método ISymUnmanagedScope::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 25a8188e3ab62c095355b72b3e63e767a6768114
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446362"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="49689-102">Método ISymUnmanagedScope::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="49689-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="49689-103">Obtém o deslocamento de fim deste escopo.</span><span class="sxs-lookup"><span data-stu-id="49689-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49689-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49689-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49689-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49689-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="49689-106">fora Um ponteiro para uma `ULONG32` que recebe o deslocamento final.</span><span class="sxs-lookup"><span data-stu-id="49689-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49689-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="49689-107">Return Value</span></span>  
 <span data-ttu-id="49689-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="49689-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49689-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="49689-109">Requirements</span></span>  
 <span data-ttu-id="49689-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="49689-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49689-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49689-111">See also</span></span>

- [<span data-ttu-id="49689-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="49689-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="49689-113">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="49689-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
