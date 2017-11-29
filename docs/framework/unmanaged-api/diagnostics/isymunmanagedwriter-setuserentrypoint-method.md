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
ms.openlocfilehash: be7f348237fdcf0a136d34ce3b6b8548c16d5547
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="565f7-102">Método ISymUnmanagedWriter::SetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="565f7-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="565f7-103">Especifica o método definido pelo usuário que é o ponto de entrada para este módulo.</span><span class="sxs-lookup"><span data-stu-id="565f7-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="565f7-104">Por exemplo, esse ponto de entrada pode ser o método do usuário principal, em vez de gerado pelo compilador stubs antes de principal.</span><span class="sxs-lookup"><span data-stu-id="565f7-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="565f7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="565f7-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="565f7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="565f7-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="565f7-107">[in] Aponte o token de metadados para o método que é a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="565f7-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="565f7-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="565f7-108">Return Value</span></span>  
 <span data-ttu-id="565f7-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="565f7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="565f7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="565f7-110">Requirements</span></span>  
 <span data-ttu-id="565f7-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="565f7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565f7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="565f7-112">See Also</span></span>  
 [<span data-ttu-id="565f7-113">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="565f7-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
