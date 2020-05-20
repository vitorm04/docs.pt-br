---
title: Método ISymUnmanagedConstant::GetValue
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 8e20d2e0f3d5cb6dc7444c8e78665b6c8b82d2de
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441468"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="b0fc3-102">Método ISymUnmanagedConstant::GetValue</span><span class="sxs-lookup"><span data-stu-id="b0fc3-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="b0fc3-103"> Obtém o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="b0fc3-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0fc3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0fc3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0fc3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0fc3-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="b0fc3-106">fora Um ponteiro para uma variável que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="b0fc3-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0fc3-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b0fc3-107">Return Value</span></span>  
 <span data-ttu-id="b0fc3-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b0fc3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0fc3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0fc3-109">Requirements</span></span>  
 <span data-ttu-id="b0fc3-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b0fc3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0fc3-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0fc3-111">See also</span></span>

- [<span data-ttu-id="b0fc3-112">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="b0fc3-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="b0fc3-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="b0fc3-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="b0fc3-114">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="b0fc3-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
