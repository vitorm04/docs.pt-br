---
title: "Método ISymUnmanagedReader2::GetMethodByVersionPreRemap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0745428c6e9a51c5c7fa413838cf65eb907eea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="d5062-102">Método ISymUnmanagedReader2::GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="d5062-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="d5062-103">Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="d5062-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="d5062-104">Números de versão começam em 1 e são incrementados cada vez que o método é alterado como resultado de uma operação Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="d5062-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5062-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5062-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5062-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5062-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="d5062-107">[in] O token de metadados de método.</span><span class="sxs-lookup"><span data-stu-id="d5062-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="d5062-108">[in] A versão do método.</span><span class="sxs-lookup"><span data-stu-id="d5062-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d5062-109">[out] Um ponteiro para retornado [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="d5062-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5062-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d5062-110">Return Value</span></span>  
 <span data-ttu-id="d5062-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d5062-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5062-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d5062-112">Requirements</span></span>  
 <span data-ttu-id="d5062-113">**Cabeçalho:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="d5062-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="d5062-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d5062-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5062-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5062-115">See Also</span></span>  
 [<span data-ttu-id="d5062-116">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="d5062-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
