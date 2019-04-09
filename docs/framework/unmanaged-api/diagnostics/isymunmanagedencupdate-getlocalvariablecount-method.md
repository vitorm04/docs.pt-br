---
title: Método ISymUnmanagedENCUpdate::GetLocalVariableCount
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a75ca89a3537ce8ee72e8ba24401800eacff20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153771"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="9b2bb-102">Método ISymUnmanagedENCUpdate::GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="9b2bb-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="9b2bb-103">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="9b2bb-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b2bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b2bb-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b2bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b2bb-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="9b2bb-106">[in] O token de metadados de métodos.</span><span class="sxs-lookup"><span data-stu-id="9b2bb-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="9b2bb-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="9b2bb-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b2bb-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9b2bb-108">Return Value</span></span>  
 <span data-ttu-id="9b2bb-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="9b2bb-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b2bb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b2bb-110">Requirements</span></span>  
 <span data-ttu-id="9b2bb-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b2bb-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b2bb-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b2bb-112">See also</span></span>

- [<span data-ttu-id="9b2bb-113">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="9b2bb-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
