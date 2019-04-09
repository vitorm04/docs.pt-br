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
ms.openlocfilehash: c5b65cdeb36b8abf17c74d41a7fc7dfb34fa5731
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095796"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="df544-102">Método ISymUnmanagedNamespace::GetVariables</span><span class="sxs-lookup"><span data-stu-id="df544-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="df544-103">Retorna todas as variáveis definidas no escopo global dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="df544-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df544-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df544-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df544-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df544-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="df544-106">[in] Um `ULONG32` que indica o tamanho do `pVars` matriz.</span><span class="sxs-lookup"><span data-stu-id="df544-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="df544-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="df544-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="df544-108">[out] Um ponteiro para um buffer que contém os namespaces.</span><span class="sxs-lookup"><span data-stu-id="df544-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df544-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df544-109">Return Value</span></span>  
 <span data-ttu-id="df544-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="df544-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df544-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df544-111">Requirements</span></span>  
 <span data-ttu-id="df544-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df544-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df544-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df544-113">See also</span></span>

- [<span data-ttu-id="df544-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="df544-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
