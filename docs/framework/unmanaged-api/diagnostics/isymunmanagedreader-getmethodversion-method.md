---
title: "Método ISymUnmanagedReader::GetMethodVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713b8a89c9519abe407ac1d68adb2552cd012b1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="25806-102">Método ISymUnmanagedReader::GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="25806-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="25806-103">Obtém a versão do método.</span><span class="sxs-lookup"><span data-stu-id="25806-103">Gets the method version.</span></span> <span data-ttu-id="25806-104">A versão do método começa em 1 e é incrementada toda vez que o método é recompilado.</span><span class="sxs-lookup"><span data-stu-id="25806-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="25806-105">A recompilação pode ocorrer sem alterações para o método.</span><span class="sxs-lookup"><span data-stu-id="25806-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25806-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25806-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25806-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25806-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="25806-108">[in] O método para o qual obter a versão.</span><span class="sxs-lookup"><span data-stu-id="25806-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="25806-109">[out] Um ponteiro para uma variável que recebe a versão do método.</span><span class="sxs-lookup"><span data-stu-id="25806-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25806-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="25806-110">Return Value</span></span>  
 <span data-ttu-id="25806-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="25806-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25806-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25806-112">Requirements</span></span>  
 <span data-ttu-id="25806-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25806-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25806-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25806-114">See Also</span></span>  
 [<span data-ttu-id="25806-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="25806-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
