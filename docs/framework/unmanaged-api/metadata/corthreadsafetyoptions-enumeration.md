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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d71d2a5b3007d4e877900443af426a9643b29125
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360427"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="2d9da-102">Enumeração CorThreadSafetyOptions</span><span class="sxs-lookup"><span data-stu-id="2d9da-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="2d9da-103">Especifica os sinalizadores para selecionar opções para acesso thread-safe.</span><span class="sxs-lookup"><span data-stu-id="2d9da-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d9da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d9da-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="2d9da-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2d9da-105">Members</span></span>

|<span data-ttu-id="2d9da-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2d9da-106">Member</span></span>|<span data-ttu-id="2d9da-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d9da-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="2d9da-108">Valor padrão.</span><span class="sxs-lookup"><span data-stu-id="2d9da-108">Default value.</span></span> <span data-ttu-id="2d9da-109">Mesmo que `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="2d9da-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="2d9da-110">Indica que um bloqueio de leitor/gravador não pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="2d9da-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="2d9da-111">Indica que um bloqueio de leitor/gravador pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="2d9da-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="2d9da-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d9da-112">Requirements</span></span>

<span data-ttu-id="2d9da-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d9da-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="2d9da-114">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2d9da-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="2d9da-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d9da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2d9da-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d9da-116">See also</span></span>

- [<span data-ttu-id="2d9da-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2d9da-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
