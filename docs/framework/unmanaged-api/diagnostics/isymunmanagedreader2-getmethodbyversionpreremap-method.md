---
title: Método ISymUnmanagedReader2::GetMethodByVersionPreRemap
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e84d912a96752a893230393b59496377b783956
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494906"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="0365d-102">Método ISymUnmanagedReader2::GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="0365d-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="0365d-103">Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="0365d-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="0365d-104">Números de versão começam em 1 e são incrementados sempre que o método é alterado como resultado de uma operação de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="0365d-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0365d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0365d-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0365d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0365d-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="0365d-107">[in] O token de metadados do método.</span><span class="sxs-lookup"><span data-stu-id="0365d-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="0365d-108">[in] A versão do método.</span><span class="sxs-lookup"><span data-stu-id="0365d-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0365d-109">[out] Um ponteiro para retornado [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0365d-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0365d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0365d-110">Return Value</span></span>  
 <span data-ttu-id="0365d-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0365d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0365d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0365d-112">Requirements</span></span>  
 <span data-ttu-id="0365d-113">**Cabeçalho:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="0365d-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="0365d-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0365d-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0365d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0365d-115">See also</span></span>
- [<span data-ttu-id="0365d-116">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="0365d-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
