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
ms.openlocfilehash: ab6228866434b35525b16e97b8cba718b849dea1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993337"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="5816c-102">Método ISymUnmanagedReader::GetMethod</span><span class="sxs-lookup"><span data-stu-id="5816c-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="5816c-103">Obtém um método de leitor de símbolo, considerando um token de método.</span><span class="sxs-lookup"><span data-stu-id="5816c-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5816c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5816c-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5816c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5816c-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="5816c-106">[in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="5816c-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5816c-107">[out] Um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="5816c-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5816c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5816c-108">Return Value</span></span>  
 <span data-ttu-id="5816c-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="5816c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5816c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5816c-110">Requirements</span></span>  
 <span data-ttu-id="5816c-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5816c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5816c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5816c-112">See also</span></span>

- [<span data-ttu-id="5816c-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="5816c-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
