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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebef54baf4e560b364845a521e4b4444ed359395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426114"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="3075a-102">Método ISymUnmanagedScope::GetMethod</span><span class="sxs-lookup"><span data-stu-id="3075a-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="3075a-103">Obtém o método que contém esse escopo.</span><span class="sxs-lookup"><span data-stu-id="3075a-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3075a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3075a-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3075a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3075a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3075a-106">[out] Um ponteiro para retornado [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="3075a-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3075a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3075a-107">Return Value</span></span>  
 <span data-ttu-id="3075a-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3075a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3075a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3075a-109">Requirements</span></span>  
 <span data-ttu-id="3075a-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3075a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3075a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3075a-111">See Also</span></span>  
 [<span data-ttu-id="3075a-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="3075a-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
