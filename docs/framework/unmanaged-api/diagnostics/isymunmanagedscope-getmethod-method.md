---
title: Método ISymUnmanagedScope::GetMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: cdbffe71540b51ff539a45861546efd761761892
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615365"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="de548-102">Método ISymUnmanagedScope::GetMethod</span><span class="sxs-lookup"><span data-stu-id="de548-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="de548-103">Obtém o método que contém esse escopo.</span><span class="sxs-lookup"><span data-stu-id="de548-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de548-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de548-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de548-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de548-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="de548-106">fora Um ponteiro para a interface [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="de548-106">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de548-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="de548-107">Return Value</span></span>  
 <span data-ttu-id="de548-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="de548-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de548-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de548-109">Requirements</span></span>  
 <span data-ttu-id="de548-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="de548-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de548-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="de548-111">See also</span></span>

- [<span data-ttu-id="de548-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="de548-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
