---
title: Método ISymUnmanagedVariable::GetEndOffset
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0f11614c6fa15034ef5fa3d68e41a936a9ff764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427851"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="3847e-102">Método ISymUnmanagedVariable::GetEndOffset</span><span class="sxs-lookup"><span data-stu-id="3847e-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="3847e-103">Obtém o deslocamento de fim desta variável dentro de seu pai.</span><span class="sxs-lookup"><span data-stu-id="3847e-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="3847e-104">Se esta é uma variável local dentro de um escopo, se o deslocamento de fim dentro os deslocamentos definidos para o escopo.</span><span class="sxs-lookup"><span data-stu-id="3847e-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3847e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3847e-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3847e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3847e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3847e-107">[out] Um ponteiro para um `ULONG32` que recebe o deslocamento de fim.</span><span class="sxs-lookup"><span data-stu-id="3847e-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3847e-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3847e-108">Return Value</span></span>  
 <span data-ttu-id="3847e-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3847e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3847e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3847e-110">Requirements</span></span>  
 <span data-ttu-id="3847e-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3847e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3847e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3847e-112">See Also</span></span>  
 [<span data-ttu-id="3847e-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="3847e-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="3847e-114">Método GetStartOffset</span><span class="sxs-lookup"><span data-stu-id="3847e-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
