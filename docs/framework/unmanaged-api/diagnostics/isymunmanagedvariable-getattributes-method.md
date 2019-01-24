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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d418a1088f9ee23a088ab4c8246810d2c9bee4fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574333"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="4e8af-102">Método ISymUnmanagedVariable::GetAttributes</span><span class="sxs-lookup"><span data-stu-id="4e8af-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="4e8af-103">Obtém os sinalizadores de atributo para essa variável.</span><span class="sxs-lookup"><span data-stu-id="4e8af-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e8af-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e8af-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e8af-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e8af-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4e8af-106">[out] Um ponteiro para um `ULONG32` que recebe os atributos.</span><span class="sxs-lookup"><span data-stu-id="4e8af-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="4e8af-107">O valor retornado será um dos valores definidos na [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="4e8af-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e8af-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4e8af-108">Return Value</span></span>  
 <span data-ttu-id="4e8af-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4e8af-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e8af-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4e8af-110">Requirements</span></span>  
 <span data-ttu-id="4e8af-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4e8af-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8af-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e8af-112">See also</span></span>
- [<span data-ttu-id="4e8af-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="4e8af-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
