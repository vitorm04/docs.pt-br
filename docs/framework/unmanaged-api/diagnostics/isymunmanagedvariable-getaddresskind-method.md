---
title: "Método ISymUnmanagedVariable::GetAddressKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressKind
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c4651641e3c430379b11698acf29eae450b02b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="a60fe-102">Método ISymUnmanagedVariable::GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="a60fe-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="a60fe-103">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="a60fe-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a60fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a60fe-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a60fe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a60fe-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a60fe-106">[out] Um ponteiro para um `ULONG32` que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="a60fe-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="a60fe-107">Os valores possíveis são definidos no [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="a60fe-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a60fe-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a60fe-108">Return Value</span></span>  
 <span data-ttu-id="a60fe-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a60fe-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a60fe-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a60fe-110">Requirements</span></span>  
 <span data-ttu-id="a60fe-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a60fe-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a60fe-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a60fe-112">See Also</span></span>  
 [<span data-ttu-id="a60fe-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="a60fe-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
