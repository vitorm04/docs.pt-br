---
title: "Método ISymUnmanagedWriter::SetUserEntryPoint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5da021bce46df02789547eb7ee50133b6f4d4af6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="58d41-102">Método ISymUnmanagedWriter::SetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="58d41-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="58d41-103">Especifica o método definido pelo usuário que é o ponto de entrada para este módulo.</span><span class="sxs-lookup"><span data-stu-id="58d41-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="58d41-104">Por exemplo, esse ponto de entrada pode ser o método do usuário principal, em vez de gerado pelo compilador stubs antes de principal.</span><span class="sxs-lookup"><span data-stu-id="58d41-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d41-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58d41-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58d41-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58d41-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="58d41-107">[in] Aponte o token de metadados para o método que é a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="58d41-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58d41-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="58d41-108">Return Value</span></span>  
 <span data-ttu-id="58d41-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="58d41-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58d41-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58d41-110">Requirements</span></span>  
 <span data-ttu-id="58d41-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="58d41-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d41-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58d41-112">See Also</span></span>  
 [<span data-ttu-id="58d41-113">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="58d41-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
