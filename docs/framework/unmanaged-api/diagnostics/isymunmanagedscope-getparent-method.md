---
title: Método ISymUnmanagedScope::GetParent
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d90aeb22a945f4fa1576009c700c420704dd891b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144775"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="b6bca-102">Método ISymUnmanagedScope::GetParent</span><span class="sxs-lookup"><span data-stu-id="b6bca-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="b6bca-103">Obtém o escopo pai desse escopo.</span><span class="sxs-lookup"><span data-stu-id="b6bca-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6bca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6bca-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6bca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6bca-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b6bca-106">[out] Um ponteiro para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b6bca-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6bca-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b6bca-107">Return Value</span></span>  
 <span data-ttu-id="b6bca-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b6bca-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6bca-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6bca-109">Requirements</span></span>  
 <span data-ttu-id="b6bca-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b6bca-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bca-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6bca-111">See also</span></span>

- [<span data-ttu-id="b6bca-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="b6bca-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="b6bca-113">Método GetChildren</span><span class="sxs-lookup"><span data-stu-id="b6bca-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
