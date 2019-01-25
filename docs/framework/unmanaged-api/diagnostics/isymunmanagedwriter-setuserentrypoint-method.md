---
title: Método ISymUnmanagedWriter::SetUserEntryPoint
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7595b4a69dd327e448aade1e2dcba06100e55bf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638672"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="394e6-102">Método ISymUnmanagedWriter::SetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="394e6-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="394e6-103">Especifica o método definido pelo usuário que é o ponto de entrada para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="394e6-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="394e6-104">Por exemplo, esse ponto de entrada pode ser o método do usuário principal, em vez de stubs gerados pelo compilador antes de principal.</span><span class="sxs-lookup"><span data-stu-id="394e6-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="394e6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="394e6-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="394e6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="394e6-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="394e6-107">[in] O token de metadados para o método que é a entrada do usuário do ponto.</span><span class="sxs-lookup"><span data-stu-id="394e6-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="394e6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="394e6-108">Return Value</span></span>  
 <span data-ttu-id="394e6-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="394e6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="394e6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="394e6-110">Requirements</span></span>  
 <span data-ttu-id="394e6-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="394e6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394e6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="394e6-112">See also</span></span>
- [<span data-ttu-id="394e6-113">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="394e6-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
