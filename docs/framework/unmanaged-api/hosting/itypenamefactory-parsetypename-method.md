---
title: Método ITypeNameFactory::ParseTypeName
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: 493c5136587eec8f1da85d15a2e7f3ecd235bcd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123310"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="c9153-102">Método ITypeNameFactory::ParseTypeName</span><span class="sxs-lookup"><span data-stu-id="c9153-102">ITypeNameFactory::ParseTypeName Method</span></span>
<span data-ttu-id="c9153-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="c9153-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9153-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9153-104">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c9153-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9153-105">Requirements</span></span>  
 <span data-ttu-id="c9153-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9153-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9153-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9153-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9153-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c9153-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9153-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9153-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9153-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9153-110">See also</span></span>

- [<span data-ttu-id="c9153-111">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="c9153-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
