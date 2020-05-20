---
title: Método ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 0be7297fbb71302035e71fbbf2c8b5e2a7faa2da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615287"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="fd785-102">Método ISymUnmanagedSymbolSearchInfo::GetSearchPathLength</span><span class="sxs-lookup"><span data-stu-id="fd785-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="fd785-103">Obtém o comprimento do caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fd785-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd785-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd785-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd785-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fd785-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="fd785-106">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o comprimento do caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fd785-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd785-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fd785-107">Return Value</span></span>  
 <span data-ttu-id="fd785-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="fd785-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd785-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fd785-109">Requirements</span></span>  
 <span data-ttu-id="fd785-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fd785-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd785-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd785-111">See also</span></span>

- [<span data-ttu-id="fd785-112">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="fd785-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
