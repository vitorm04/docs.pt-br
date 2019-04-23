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
ms.openlocfilehash: 0267ae8b57c837b097d496c8e119085d03417e36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211264"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="d5819-102">Método ISymUnmanagedReader::GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="d5819-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="d5819-103">Retorna o método que foi especificado como o ponto de entrada do usuário para o módulo, se houver.</span><span class="sxs-lookup"><span data-stu-id="d5819-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="d5819-104">Por exemplo, esse método pode ser o principal método de usuário em vez de stubs gerados pelo compilador antes que o método principal.</span><span class="sxs-lookup"><span data-stu-id="d5819-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5819-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5819-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5819-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5819-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="d5819-107">[out] Um ponteiro para uma variável que recebe o ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="d5819-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5819-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5819-108">Return Value</span></span>  
 <span data-ttu-id="d5819-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d5819-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5819-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5819-110">Requirements</span></span>  
 <span data-ttu-id="d5819-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d5819-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5819-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5819-112">See also</span></span>

- [<span data-ttu-id="d5819-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="d5819-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
