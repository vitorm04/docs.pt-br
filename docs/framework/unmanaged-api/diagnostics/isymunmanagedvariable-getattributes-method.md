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
ms.openlocfilehash: cfc28dfcda7bf4b3d1fc6fe3530a212ee76fadd2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446077"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="1c313-102">Método ISymUnmanagedVariable::GetAttributes</span><span class="sxs-lookup"><span data-stu-id="1c313-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="1c313-103">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="1c313-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c313-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c313-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c313-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c313-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1c313-106">fora Um ponteiro para um `ULONG32` que recebe os atributos.</span><span class="sxs-lookup"><span data-stu-id="1c313-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="1c313-107">O valor retornado será um dos valores definidos na enumeração [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1c313-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c313-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1c313-108">Return Value</span></span>  
 <span data-ttu-id="1c313-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1c313-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c313-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1c313-110">Requirements</span></span>  
 <span data-ttu-id="1c313-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1c313-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c313-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c313-112">See also</span></span>

- [<span data-ttu-id="1c313-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="1c313-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
