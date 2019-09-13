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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 813f57377c1885b09190ada3c73f4391a3f2d931
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895053"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="920fe-102">Método ISymUnmanagedNamespace::GetVariables</span><span class="sxs-lookup"><span data-stu-id="920fe-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="920fe-103">Retorna todas as variáveis definidas no escopo global dentro deste namespace.</span><span class="sxs-lookup"><span data-stu-id="920fe-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="920fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="920fe-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="920fe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="920fe-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="920fe-106">no Um `ULONG32` que indica o tamanho `pVars` da matriz.</span><span class="sxs-lookup"><span data-stu-id="920fe-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="920fe-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="920fe-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="920fe-108">fora Um ponteiro para um buffer que contém os namespaces.</span><span class="sxs-lookup"><span data-stu-id="920fe-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="920fe-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="920fe-109">Return Value</span></span>  
 <span data-ttu-id="920fe-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="920fe-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="920fe-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="920fe-111">Requirements</span></span>  
 <span data-ttu-id="920fe-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="920fe-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="920fe-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="920fe-113">See also</span></span>

- [<span data-ttu-id="920fe-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="920fe-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
