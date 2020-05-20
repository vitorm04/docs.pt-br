---
title: Método ISymUnmanagedScope2::GetConstantCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: 88fc6b7d6076bca42050ca87533062557e6a7b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610945"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="dfcf7-102">Método ISymUnmanagedScope2::GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="dfcf7-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="dfcf7-103">Obtém uma contagem das constantes definidas neste escopo.</span><span class="sxs-lookup"><span data-stu-id="dfcf7-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfcf7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfcf7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfcf7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dfcf7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dfcf7-106">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter as constantes.</span><span class="sxs-lookup"><span data-stu-id="dfcf7-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfcf7-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="dfcf7-107">Return Value</span></span>  
 <span data-ttu-id="dfcf7-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="dfcf7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfcf7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dfcf7-109">Requirements</span></span>  
 <span data-ttu-id="dfcf7-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dfcf7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcf7-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="dfcf7-111">See also</span></span>

- [<span data-ttu-id="dfcf7-112">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="dfcf7-112">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
