---
title: Enumeração CorThreadSafetyOptions
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 93dd8c56176890d04d792f3c336492e4f232825b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442474"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="c95ce-102">Enumeração CorThreadSafetyOptions</span><span class="sxs-lookup"><span data-stu-id="c95ce-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="c95ce-103">Specifies flags to select options for thread safety.</span><span class="sxs-lookup"><span data-stu-id="c95ce-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="c95ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c95ce-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="c95ce-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c95ce-105">Members</span></span>

|<span data-ttu-id="c95ce-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c95ce-106">Member</span></span>|<span data-ttu-id="c95ce-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c95ce-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="c95ce-108">Valor padrão.</span><span class="sxs-lookup"><span data-stu-id="c95ce-108">Default value.</span></span> <span data-ttu-id="c95ce-109">Mesmo que `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="c95ce-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="c95ce-110">Indicates that a reader/writer lock cannot be set.</span><span class="sxs-lookup"><span data-stu-id="c95ce-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="c95ce-111">Indicates that a reader/writer lock can be set.</span><span class="sxs-lookup"><span data-stu-id="c95ce-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="c95ce-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c95ce-112">Requirements</span></span>

<span data-ttu-id="c95ce-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c95ce-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="c95ce-114">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c95ce-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="c95ce-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c95ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c95ce-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c95ce-116">See also</span></span>

- [<span data-ttu-id="c95ce-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="c95ce-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
