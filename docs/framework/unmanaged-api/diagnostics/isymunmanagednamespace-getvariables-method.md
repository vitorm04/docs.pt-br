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
ms.openlocfilehash: 2b63dbcaa54e03e5603e06545f8b4fec393d8268
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424603"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="aa470-102">Método ISymUnmanagedNamespace::GetVariables</span><span class="sxs-lookup"><span data-stu-id="aa470-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="aa470-103">Retorna todas as variáveis definidas no escopo global dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="aa470-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa470-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa470-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa470-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa470-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="aa470-106">[in] Um `ULONG32` que indica o tamanho do `pVars` matriz.</span><span class="sxs-lookup"><span data-stu-id="aa470-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="aa470-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="aa470-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="aa470-108">[out] Um ponteiro para um buffer que contém os namespaces.</span><span class="sxs-lookup"><span data-stu-id="aa470-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa470-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="aa470-109">Return Value</span></span>  
 <span data-ttu-id="aa470-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="aa470-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa470-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aa470-111">Requirements</span></span>  
 <span data-ttu-id="aa470-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aa470-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa470-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa470-113">See Also</span></span>  
 [<span data-ttu-id="aa470-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="aa470-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
