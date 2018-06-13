---
title: Método ISymUnmanagedScope2::GetConstantCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbe41a3102a61052b2eceae7ccce3b93fd1bef6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426095"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="bae0e-102">Método ISymUnmanagedScope2::GetConstantCount</span><span class="sxs-lookup"><span data-stu-id="bae0e-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="bae0e-103">Obtém uma contagem das constantes definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="bae0e-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bae0e-104">Syntax</span></span>  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bae0e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bae0e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bae0e-106">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter as constantes.</span><span class="sxs-lookup"><span data-stu-id="bae0e-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bae0e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bae0e-107">Return Value</span></span>  
 <span data-ttu-id="bae0e-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="bae0e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bae0e-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bae0e-109">Requirements</span></span>  
 <span data-ttu-id="bae0e-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bae0e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae0e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bae0e-111">See Also</span></span>  
 [<span data-ttu-id="bae0e-112">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="bae0e-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
