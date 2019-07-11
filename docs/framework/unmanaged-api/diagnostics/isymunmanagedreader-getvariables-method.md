---
title: Método ISymUnmanagedReader::GetVariables
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1db08dfcd2adf1247dd717d6c826bce4726b8a1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777046"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="3a1e5-102">Método ISymUnmanagedReader::GetVariables</span><span class="sxs-lookup"><span data-stu-id="3a1e5-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="3a1e5-103">Retorna uma variável não local, dado seu pai e o nome.</span><span class="sxs-lookup"><span data-stu-id="3a1e5-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a1e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a1e5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3a1e5-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="3a1e5-106">[in] O pai da variável.</span><span class="sxs-lookup"><span data-stu-id="3a1e5-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="3a1e5-107">[in] O tamanho do `pVars` matriz.</span><span class="sxs-lookup"><span data-stu-id="3a1e5-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="3a1e5-108">[out] Um ponteiro para a variável que recebe o número de variáveis retornadas em `pVars`.</span><span class="sxs-lookup"><span data-stu-id="3a1e5-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="3a1e5-109">[out] Um ponteiro para a variável que recebe as variáveis.</span><span class="sxs-lookup"><span data-stu-id="3a1e5-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a1e5-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3a1e5-110">Return Value</span></span>  
 <span data-ttu-id="3a1e5-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3a1e5-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a1e5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a1e5-112">Requirements</span></span>  
 <span data-ttu-id="3a1e5-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3a1e5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1e5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a1e5-114">See also</span></span>

- [<span data-ttu-id="3a1e5-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="3a1e5-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
