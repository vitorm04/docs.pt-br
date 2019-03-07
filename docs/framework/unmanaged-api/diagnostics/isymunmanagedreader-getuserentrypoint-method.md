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
ms.openlocfilehash: ea0cba1f1b9154ccb14d75f7c377a8153c24f2b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499467"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="f8b59-102">Método ISymUnmanagedReader::GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="f8b59-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="f8b59-103">Retorna o método que foi especificado como o ponto de entrada do usuário para o módulo, se houver.</span><span class="sxs-lookup"><span data-stu-id="f8b59-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="f8b59-104">Por exemplo, esse método pode ser o principal método de usuário em vez de stubs gerados pelo compilador antes que o método principal.</span><span class="sxs-lookup"><span data-stu-id="f8b59-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b59-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8b59-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8b59-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8b59-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="f8b59-107">[out] Um ponteiro para uma variável que recebe o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="f8b59-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8b59-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f8b59-108">Return Value</span></span>  
 <span data-ttu-id="f8b59-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f8b59-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8b59-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8b59-110">Requirements</span></span>  
 <span data-ttu-id="f8b59-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8b59-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b59-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8b59-112">See also</span></span>
- [<span data-ttu-id="f8b59-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f8b59-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
