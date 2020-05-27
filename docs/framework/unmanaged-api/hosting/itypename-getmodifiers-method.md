---
title: Método ITypeName::GetModifiers
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 8544b8d7b1f23853465bbb2aea697dfe021d77f2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842173"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="b504a-102">Método ITypeName::GetModifiers</span><span class="sxs-lookup"><span data-stu-id="b504a-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="b504a-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="b504a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b504a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b504a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b504a-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b504a-105">Requirements</span></span>  
 <span data-ttu-id="b504a-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b504a-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b504a-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b504a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b504a-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b504a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b504a-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b504a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b504a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b504a-110">See also</span></span>

- [<span data-ttu-id="b504a-111">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="b504a-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
