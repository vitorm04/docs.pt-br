---
title: Método ISymUnmanagedVariable::GetStartOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: f2996349fd2bf1765a3de5b67d3296a25b1eaa5e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610360"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="48869-102">Método ISymUnmanagedVariable::GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="48869-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="48869-103">Obtém o deslocamento inicial dessa variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="48869-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="48869-104">Se essa for uma variável local dentro de um escopo, o deslocamento de início se enquadrará dentro dos deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="48869-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48869-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48869-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48869-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48869-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="48869-107">fora Um ponteiro para um `ULONG32` que recebe o deslocamento de início.</span><span class="sxs-lookup"><span data-stu-id="48869-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48869-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="48869-108">Return Value</span></span>  
 <span data-ttu-id="48869-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="48869-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48869-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48869-110">Requirements</span></span>  
 <span data-ttu-id="48869-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="48869-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48869-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="48869-112">See also</span></span>

- [<span data-ttu-id="48869-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="48869-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="48869-114">Método GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="48869-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
