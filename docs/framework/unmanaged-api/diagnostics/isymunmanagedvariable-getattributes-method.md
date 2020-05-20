---
title: Método ISymUnmanagedVariable::GetAttributes
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 29869abdd39f61c6c9cb51d6b2be50fa462c5b70
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615248"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="c4e90-102">Método ISymUnmanagedVariable::GetAttributes</span><span class="sxs-lookup"><span data-stu-id="c4e90-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="c4e90-103">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="c4e90-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e90-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4e90-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4e90-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4e90-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c4e90-106">fora Um ponteiro para um `ULONG32` que recebe os atributos.</span><span class="sxs-lookup"><span data-stu-id="c4e90-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="c4e90-107">O valor retornado será um dos valores definidos na enumeração [CorSymVarFlag](corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c4e90-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4e90-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c4e90-108">Return Value</span></span>  
 <span data-ttu-id="c4e90-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c4e90-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e90-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4e90-110">Requirements</span></span>  
 <span data-ttu-id="c4e90-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c4e90-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e90-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="c4e90-112">See also</span></span>

- [<span data-ttu-id="c4e90-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="c4e90-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
