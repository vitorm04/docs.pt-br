---
title: Método ISymUnmanagedScope::GetLocalCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 809b9033c784954374065a901f34f7542f41e7ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549930"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="d1c13-102">Método ISymUnmanagedScope::GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="d1c13-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="d1c13-103">Obtém uma contagem das variáveis locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="d1c13-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1c13-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1c13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1c13-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d1c13-106">[out] Um ponteiro para um `ULONG32` que recebe a contagem de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="d1c13-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1c13-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d1c13-107">Return Value</span></span>  
 <span data-ttu-id="d1c13-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d1c13-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c13-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1c13-109">Requirements</span></span>  
 <span data-ttu-id="d1c13-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1c13-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c13-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1c13-111">See also</span></span>
- [<span data-ttu-id="d1c13-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="d1c13-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
