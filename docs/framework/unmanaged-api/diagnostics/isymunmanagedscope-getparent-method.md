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
ms.openlocfilehash: 512dd4055a0aad8498db6ef2241c9363aecee9c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446294"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="0f805-102">Método ISymUnmanagedScope::GetParent</span><span class="sxs-lookup"><span data-stu-id="0f805-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="0f805-103">Obtém o escopo pai deste escopo.</span><span class="sxs-lookup"><span data-stu-id="0f805-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f805-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f805-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f805-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f805-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0f805-106">fora Um ponteiro para a interface [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="0f805-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f805-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="0f805-107">Return Value</span></span>  
 <span data-ttu-id="0f805-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0f805-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f805-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="0f805-109">Requirements</span></span>  
 <span data-ttu-id="0f805-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0f805-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f805-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f805-111">See also</span></span>

- [<span data-ttu-id="0f805-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="0f805-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="0f805-113">Método GetChildren</span><span class="sxs-lookup"><span data-stu-id="0f805-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
