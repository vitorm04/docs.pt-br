---
title: Método ISymUnmanagedReader::GetMethodVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45aaceb2c39703cb1369941ce801c9cff1935ad6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555837"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="ffe0c-102">Método ISymUnmanagedReader::GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="ffe0c-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="ffe0c-103">Obtém a versão do método.</span><span class="sxs-lookup"><span data-stu-id="ffe0c-103">Gets the method version.</span></span> <span data-ttu-id="ffe0c-104">A versão do método começa em 1 e é incrementada toda vez que o método for recompilado.</span><span class="sxs-lookup"><span data-stu-id="ffe0c-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="ffe0c-105">A recompilação pode acontecer sem alterações para o método.</span><span class="sxs-lookup"><span data-stu-id="ffe0c-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe0c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffe0c-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffe0c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ffe0c-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="ffe0c-108">[in] O método para o qual obter a versão.</span><span class="sxs-lookup"><span data-stu-id="ffe0c-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="ffe0c-109">[out] Um ponteiro para uma variável que recebe a versão do método.</span><span class="sxs-lookup"><span data-stu-id="ffe0c-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffe0c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ffe0c-110">Return Value</span></span>  
 <span data-ttu-id="ffe0c-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="ffe0c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe0c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ffe0c-112">Requirements</span></span>  
 <span data-ttu-id="ffe0c-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ffe0c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe0c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffe0c-114">See also</span></span>
- [<span data-ttu-id="ffe0c-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="ffe0c-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
