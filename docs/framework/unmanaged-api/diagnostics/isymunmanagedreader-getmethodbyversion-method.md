---
title: Método ISymUnmanagedReader::GetMethodByVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5888c33e9532e5fc132fe571d59699d6f80c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="4c8ea-102">Método ISymUnmanagedReader::GetMethodByVersion</span><span class="sxs-lookup"><span data-stu-id="4c8ea-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="4c8ea-103">Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de editar e copiar.</span><span class="sxs-lookup"><span data-stu-id="4c8ea-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="4c8ea-104">Números de versão começam em 1 e são incrementados cada vez que o método é alterado como resultado de uma operação de cópia e de edição.</span><span class="sxs-lookup"><span data-stu-id="4c8ea-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c8ea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c8ea-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c8ea-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4c8ea-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="4c8ea-107">[in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="4c8ea-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="4c8ea-108">[in] A versão do método.</span><span class="sxs-lookup"><span data-stu-id="4c8ea-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4c8ea-109">[out] Um ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="4c8ea-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c8ea-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4c8ea-110">Return Value</span></span>  
 <span data-ttu-id="4c8ea-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4c8ea-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c8ea-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c8ea-112">Requirements</span></span>  
 <span data-ttu-id="4c8ea-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4c8ea-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8ea-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c8ea-114">See Also</span></span>  
 [<span data-ttu-id="4c8ea-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="4c8ea-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
