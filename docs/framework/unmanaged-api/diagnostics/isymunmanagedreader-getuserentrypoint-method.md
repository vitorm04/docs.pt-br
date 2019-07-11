---
title: Método ISymUnmanagedReader::GetUserEntryPoint
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 995c7edf99c917b8bcdc1d51dcc0bf50868e4f35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777059"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="b97ce-102">Método ISymUnmanagedReader::GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="b97ce-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="b97ce-103">Retorna o método que foi especificado como o ponto de entrada do usuário para o módulo, se houver.</span><span class="sxs-lookup"><span data-stu-id="b97ce-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="b97ce-104">Por exemplo, esse método pode ser o principal método de usuário em vez de stubs gerados pelo compilador antes que o método principal.</span><span class="sxs-lookup"><span data-stu-id="b97ce-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b97ce-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b97ce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b97ce-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b97ce-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="b97ce-107">[out] Um ponteiro para uma variável que recebe o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="b97ce-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b97ce-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b97ce-108">Return Value</span></span>  
 <span data-ttu-id="b97ce-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b97ce-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b97ce-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b97ce-110">Requirements</span></span>  
 <span data-ttu-id="b97ce-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b97ce-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b97ce-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b97ce-112">See also</span></span>

- [<span data-ttu-id="b97ce-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="b97ce-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
