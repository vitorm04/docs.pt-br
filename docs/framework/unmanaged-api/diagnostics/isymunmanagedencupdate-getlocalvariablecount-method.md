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
ms.openlocfilehash: d7d557e2111a26c0865c20d8eb952c4d42b5604e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="f489a-102">Método ISymUnmanagedENCUpdate::GetLocalVariableCount</span><span class="sxs-lookup"><span data-stu-id="f489a-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="f489a-103">Obtém o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f489a-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f489a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f489a-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f489a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f489a-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="f489a-106">[in] O token de metadados de métodos.</span><span class="sxs-lookup"><span data-stu-id="f489a-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="f489a-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter o número de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f489a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f489a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f489a-108">Return Value</span></span>  
 <span data-ttu-id="f489a-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f489a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f489a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f489a-110">Requirements</span></span>  
 <span data-ttu-id="f489a-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f489a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f489a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f489a-112">See Also</span></span>  
 [<span data-ttu-id="f489a-113">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="f489a-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
