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
ms.openlocfilehash: d14d542a8c1d8adeaf56dc1564e8e10121cd4064
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650720"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="d5579-102">Método ISymUnmanagedWriter::SetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="d5579-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="d5579-103">Especifica o método definido pelo usuário que é o ponto de entrada para esse módulo.</span><span class="sxs-lookup"><span data-stu-id="d5579-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="d5579-104">Por exemplo, esse ponto de entrada pode ser o método do usuário principal, em vez de stubs gerados pelo compilador antes de principal.</span><span class="sxs-lookup"><span data-stu-id="d5579-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5579-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5579-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5579-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5579-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="d5579-107">[in] O token de metadados para o método que é a entrada do usuário do ponto.</span><span class="sxs-lookup"><span data-stu-id="d5579-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5579-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5579-108">Return Value</span></span>  
 <span data-ttu-id="d5579-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d5579-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5579-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5579-110">Requirements</span></span>  
 <span data-ttu-id="d5579-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d5579-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5579-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5579-112">See also</span></span>

- [<span data-ttu-id="d5579-113">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="d5579-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
