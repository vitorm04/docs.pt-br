---
title: Método IAssemblyName::GetName
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88a46ecadaf2b191e8321c5629bc77b0c67dfd3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697362"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="11477-102">Método IAssemblyName::GetName</span><span class="sxs-lookup"><span data-stu-id="11477-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="11477-103">Obtém o nome simple e não criptografado do assembly referenciado por este [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="11477-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11477-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11477-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11477-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11477-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="11477-106">[no, out] O tamanho de `pwzName` em caracteres largos, incluindo o caractere terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="11477-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="11477-107">[out] Um buffer para armazenar o nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="11477-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11477-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11477-108">Requirements</span></span>  
 <span data-ttu-id="11477-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11477-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11477-110">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="11477-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="11477-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11477-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11477-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11477-112">See also</span></span>

- [<span data-ttu-id="11477-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="11477-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
