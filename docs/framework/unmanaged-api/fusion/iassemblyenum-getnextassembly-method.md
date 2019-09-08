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
ms.openlocfilehash: 73c531378355100fdfca264ea9f96ff4d7c7ceda
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796679"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="32660-102">Método IAssemblyEnum::GetNextAssembly</span><span class="sxs-lookup"><span data-stu-id="32660-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="32660-103">Obtém um ponteiro para o próximo [IAssemblyName](iassemblyname-interface.md) contido neste objeto [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="32660-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32660-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32660-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32660-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32660-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="32660-106">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="32660-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="32660-107">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="32660-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="32660-108">fora O ponteiro `IAssemblyName` retornado.</span><span class="sxs-lookup"><span data-stu-id="32660-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="32660-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="32660-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="32660-110">`dwFlags`deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="32660-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32660-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32660-111">Requirements</span></span>  
 <span data-ttu-id="32660-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32660-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32660-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="32660-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="32660-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32660-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32660-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32660-115">See also</span></span>

- [<span data-ttu-id="32660-116">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="32660-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="32660-117">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="32660-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
