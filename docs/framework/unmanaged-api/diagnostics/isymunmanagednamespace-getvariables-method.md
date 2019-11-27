---
title: Método ISymUnmanagedNamespace::GetVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 98ed5556020b93fb1f31d1dde84690fc33092627
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448366"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="32208-102">Método ISymUnmanagedNamespace::GetVariables</span><span class="sxs-lookup"><span data-stu-id="32208-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="32208-103">Retorna todas as variáveis definidas no escopo global dentro deste namespace.</span><span class="sxs-lookup"><span data-stu-id="32208-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32208-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32208-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32208-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32208-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="32208-106">no Um `ULONG32` que indica o tamanho da matriz de `pVars`.</span><span class="sxs-lookup"><span data-stu-id="32208-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="32208-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="32208-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="32208-108">fora Um ponteiro para um buffer que contém os namespaces.</span><span class="sxs-lookup"><span data-stu-id="32208-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32208-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="32208-109">Return Value</span></span>  
 <span data-ttu-id="32208-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="32208-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32208-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="32208-111">Requirements</span></span>  
 <span data-ttu-id="32208-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="32208-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32208-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32208-113">See also</span></span>

- [<span data-ttu-id="32208-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="32208-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
