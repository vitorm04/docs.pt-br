---
title: Método ISymUnmanagedMethod::GetToken
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e276e93bc1b05dd34e1111cc53c880f8836bf09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494880"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="30b68-102">Método ISymUnmanagedMethod::GetToken</span><span class="sxs-lookup"><span data-stu-id="30b68-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="30b68-103">Retorna o token de metadados para esse método.</span><span class="sxs-lookup"><span data-stu-id="30b68-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30b68-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30b68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30b68-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="30b68-106">[out] Um ponteiro para um `mdMethodDef` que recebe o tamanho, em caracteres, do buffer necessário para conter os metadados.</span><span class="sxs-lookup"><span data-stu-id="30b68-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30b68-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="30b68-107">Return Value</span></span>  
 <span data-ttu-id="30b68-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="30b68-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30b68-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30b68-109">Requirements</span></span>  
 <span data-ttu-id="30b68-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="30b68-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b68-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30b68-111">See also</span></span>
- [<span data-ttu-id="30b68-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="30b68-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
