---
title: Método ISymUnmanagedReader::GetMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9f1056d8d5ec4486e748d3b079507943a8a72ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430632"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="db16e-102">Método ISymUnmanagedReader::GetMethod</span><span class="sxs-lookup"><span data-stu-id="db16e-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="db16e-103">Obtém um método de leitor de símbolo, recebe um token de método.</span><span class="sxs-lookup"><span data-stu-id="db16e-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db16e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db16e-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db16e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db16e-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="db16e-106">[in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="db16e-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="db16e-107">[out] Um ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="db16e-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db16e-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db16e-108">Return Value</span></span>  
 <span data-ttu-id="db16e-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="db16e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db16e-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db16e-110">Requirements</span></span>  
 <span data-ttu-id="db16e-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db16e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db16e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db16e-112">See Also</span></span>  
 [<span data-ttu-id="db16e-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="db16e-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
