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
ms.openlocfilehash: 091f497024b48589953456e1ea6daf6635738240
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615079"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="e82b6-102">Método ISymUnmanagedNamespace::GetVariables</span><span class="sxs-lookup"><span data-stu-id="e82b6-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="e82b6-103">Retorna todas as variáveis definidas no escopo global dentro deste namespace.</span><span class="sxs-lookup"><span data-stu-id="e82b6-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e82b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e82b6-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e82b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e82b6-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="e82b6-106">no Um `ULONG32` que indica o tamanho da `pVars` matriz.</span><span class="sxs-lookup"><span data-stu-id="e82b6-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="e82b6-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os namespaces.</span><span class="sxs-lookup"><span data-stu-id="e82b6-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="e82b6-108">fora Um ponteiro para um buffer que contém os namespaces.</span><span class="sxs-lookup"><span data-stu-id="e82b6-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e82b6-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="e82b6-109">Return Value</span></span>  
 <span data-ttu-id="e82b6-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e82b6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e82b6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e82b6-111">Requirements</span></span>  
 <span data-ttu-id="e82b6-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e82b6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82b6-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="e82b6-113">See also</span></span>

- [<span data-ttu-id="e82b6-114">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="e82b6-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
