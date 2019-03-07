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
ms.openlocfilehash: 031e51919d9abd7092756cc42fb35dcc0592758c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503041"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="11a00-102">Método ISymUnmanagedReader::GetMethod</span><span class="sxs-lookup"><span data-stu-id="11a00-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="11a00-103">Obtém um método de leitor de símbolo, considerando um token de método.</span><span class="sxs-lookup"><span data-stu-id="11a00-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a00-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11a00-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11a00-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11a00-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="11a00-106">[in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="11a00-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="11a00-107">[out] Um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="11a00-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11a00-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="11a00-108">Return Value</span></span>  
 <span data-ttu-id="11a00-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="11a00-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a00-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11a00-110">Requirements</span></span>  
 <span data-ttu-id="11a00-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="11a00-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a00-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11a00-112">See also</span></span>
- [<span data-ttu-id="11a00-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="11a00-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
