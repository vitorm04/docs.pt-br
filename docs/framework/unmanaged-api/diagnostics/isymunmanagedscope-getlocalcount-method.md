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
ms.openlocfilehash: 4c41c05d40187aaed8a4f3cce181c84460503d1f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751278"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="bfdbc-102">Método ISymUnmanagedScope::GetLocalCount</span><span class="sxs-lookup"><span data-stu-id="bfdbc-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="bfdbc-103">Obtém uma contagem das variáveis locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="bfdbc-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfdbc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfdbc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfdbc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfdbc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bfdbc-106">[out] Um ponteiro para um `ULONG32` que recebe a contagem de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="bfdbc-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfdbc-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bfdbc-107">Return Value</span></span>  
 <span data-ttu-id="bfdbc-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="bfdbc-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfdbc-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfdbc-109">Requirements</span></span>  
 <span data-ttu-id="bfdbc-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bfdbc-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfdbc-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfdbc-111">See also</span></span>

- [<span data-ttu-id="bfdbc-112">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="bfdbc-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
