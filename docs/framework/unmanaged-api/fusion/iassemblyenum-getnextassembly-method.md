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
ms.openlocfilehash: 563784dd2fe3881cbf3278992ca2c75a94df1d3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727554"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="47890-102">Método IAssemblyEnum::GetNextAssembly</span><span class="sxs-lookup"><span data-stu-id="47890-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="47890-103">Obtém um ponteiro para a próxima [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contido nesse [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="47890-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47890-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47890-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47890-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47890-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="47890-106">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="47890-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="47890-107">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="47890-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="47890-108">[out] Retornado `IAssemblyName` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="47890-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="47890-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="47890-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="47890-110">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="47890-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47890-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47890-111">Requirements</span></span>  
 <span data-ttu-id="47890-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47890-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47890-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="47890-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="47890-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47890-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47890-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47890-115">See also</span></span>
- [<span data-ttu-id="47890-116">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="47890-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="47890-117">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="47890-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
