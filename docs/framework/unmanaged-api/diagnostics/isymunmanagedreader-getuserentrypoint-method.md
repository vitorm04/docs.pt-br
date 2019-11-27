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
ms.openlocfilehash: 50f41bb55b7c3dc45646a465032074ce90be0abf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444511"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="87776-102">Método ISymUnmanagedReader::GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="87776-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="87776-103">Retorna o método que foi especificado como o ponto de entrada do usuário para o módulo, se houver.</span><span class="sxs-lookup"><span data-stu-id="87776-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="87776-104">Por exemplo, esse método pode ser o método Main do usuário em vez de stubs gerados pelo compilador antes do método Main.</span><span class="sxs-lookup"><span data-stu-id="87776-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87776-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87776-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87776-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87776-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="87776-107">fora Um ponteiro para uma variável que recebe o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="87776-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87776-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="87776-108">Return Value</span></span>  
 <span data-ttu-id="87776-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="87776-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87776-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="87776-110">Requirements</span></span>  
 <span data-ttu-id="87776-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="87776-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87776-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87776-112">See also</span></span>

- [<span data-ttu-id="87776-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="87776-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
