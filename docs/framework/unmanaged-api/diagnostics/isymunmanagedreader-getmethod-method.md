---
title: "Método ISymUnmanagedReader::GetMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94c40555ee62bac99cf7cb34378c5b0fcca5104f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="d29f0-102">Método ISymUnmanagedReader::GetMethod</span><span class="sxs-lookup"><span data-stu-id="d29f0-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="d29f0-103">Obtém um método de leitor de símbolo, recebe um token de método.</span><span class="sxs-lookup"><span data-stu-id="d29f0-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d29f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d29f0-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d29f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d29f0-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="d29f0-106">[in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="d29f0-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d29f0-107">[out] Um ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="d29f0-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d29f0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d29f0-108">Return Value</span></span>  
 <span data-ttu-id="d29f0-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d29f0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d29f0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d29f0-110">Requirements</span></span>  
 <span data-ttu-id="d29f0-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d29f0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29f0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d29f0-112">See Also</span></span>  
 [<span data-ttu-id="d29f0-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="d29f0-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
