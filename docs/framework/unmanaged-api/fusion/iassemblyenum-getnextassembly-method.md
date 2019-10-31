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
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134431"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="542b7-102">Método IAssemblyEnum::GetNextAssembly</span><span class="sxs-lookup"><span data-stu-id="542b7-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="542b7-103">Obtém um ponteiro para o próximo [IAssemblyName](iassemblyname-interface.md) contido neste objeto [IAssemblyEnum](iassemblyenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="542b7-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="542b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="542b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="542b7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="542b7-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="542b7-106">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="542b7-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="542b7-107">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="542b7-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="542b7-108">fora O ponteiro de `IAssemblyName` retornado.</span><span class="sxs-lookup"><span data-stu-id="542b7-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="542b7-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="542b7-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="542b7-110">`dwFlags` deve ser 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="542b7-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="542b7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="542b7-111">Requirements</span></span>  
 <span data-ttu-id="542b7-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="542b7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="542b7-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="542b7-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="542b7-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="542b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542b7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="542b7-115">See also</span></span>

- [<span data-ttu-id="542b7-116">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="542b7-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="542b7-117">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="542b7-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
