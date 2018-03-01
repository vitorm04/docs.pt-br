---
title: "Método ISymUnmanagedScope2::GetConstants"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: da0d2d39fcc1de8435c7af49a912764c79eb6583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="3aab9-102">Método ISymUnmanagedScope2::GetConstants</span><span class="sxs-lookup"><span data-stu-id="3aab9-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="3aab9-103">Obtém as constantes locais definidas dentro desse escopo.</span><span class="sxs-lookup"><span data-stu-id="3aab9-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aab9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3aab9-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3aab9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3aab9-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="3aab9-106">[in] O comprimento do buffer que o `pcConstants` parâmetro aponta para.</span><span class="sxs-lookup"><span data-stu-id="3aab9-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="3aab9-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter as constantes.</span><span class="sxs-lookup"><span data-stu-id="3aab9-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="3aab9-108">[out] O buffer que armazena as constantes.</span><span class="sxs-lookup"><span data-stu-id="3aab9-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aab9-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3aab9-109">Return Value</span></span>  
 <span data-ttu-id="3aab9-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="3aab9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aab9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3aab9-111">Requirements</span></span>  
 <span data-ttu-id="3aab9-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3aab9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aab9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aab9-113">See Also</span></span>  
 [<span data-ttu-id="3aab9-114">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="3aab9-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
