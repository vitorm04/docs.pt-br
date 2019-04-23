---
title: Método IAssemblyEnum::GetNextAssembly
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a77e468363b59e76e55aa24d97d064189ad297e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117735"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="901a6-102">Método IAssemblyEnum::GetNextAssembly</span><span class="sxs-lookup"><span data-stu-id="901a6-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="901a6-103">Obtém um ponteiro para a próxima [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contido nesse [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="901a6-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="901a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="901a6-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="901a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="901a6-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="901a6-106">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="901a6-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="901a6-107">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="901a6-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="901a6-108">[out] Retornado `IAssemblyName` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="901a6-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="901a6-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="901a6-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="901a6-110">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="901a6-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="901a6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="901a6-111">Requirements</span></span>  
 <span data-ttu-id="901a6-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="901a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="901a6-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="901a6-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="901a6-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="901a6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901a6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="901a6-115">See also</span></span>

- [<span data-ttu-id="901a6-116">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="901a6-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="901a6-117">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="901a6-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
