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
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007501"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="7c9ce-102">Enumeração CorThreadSafetyOptions</span><span class="sxs-lookup"><span data-stu-id="7c9ce-102">CorThreadSafetyOptions Enumeration</span></span>

<span data-ttu-id="7c9ce-103">Especifica sinalizadores para selecionar opções para a segurança do thread.</span><span class="sxs-lookup"><span data-stu-id="7c9ce-103">Specifies flags to select options for thread safety.</span></span>

## <a name="syntax"></a><span data-ttu-id="7c9ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c9ce-104">Syntax</span></span>

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a><span data-ttu-id="7c9ce-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7c9ce-105">Members</span></span>

|<span data-ttu-id="7c9ce-106">Membro</span><span class="sxs-lookup"><span data-stu-id="7c9ce-106">Member</span></span>|<span data-ttu-id="7c9ce-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c9ce-107">Description</span></span>|
|------------|-----------------|
|`MDThreadSafetyDefault`|<span data-ttu-id="7c9ce-108">Valor padrão.</span><span class="sxs-lookup"><span data-stu-id="7c9ce-108">Default value.</span></span> <span data-ttu-id="7c9ce-109">Igual a `MDThreadSafetyOff`.</span><span class="sxs-lookup"><span data-stu-id="7c9ce-109">Same as `MDThreadSafetyOff`.</span></span>|
|`MDThreadSafetyOff`|<span data-ttu-id="7c9ce-110">Indica que um bloqueio de leitor/gravador não pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="7c9ce-110">Indicates that a reader/writer lock cannot be set.</span></span>|
|`MDThreadSafetyOn`|<span data-ttu-id="7c9ce-111">Indica que um bloqueio de leitor/gravador pode ser definido.</span><span class="sxs-lookup"><span data-stu-id="7c9ce-111">Indicates that a reader/writer lock can be set.</span></span>|

## <a name="requirements"></a><span data-ttu-id="7c9ce-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7c9ce-112">Requirements</span></span>

<span data-ttu-id="7c9ce-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9ce-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7c9ce-114">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="7c9ce-114">**Header:** CorHdr.h</span></span>

<span data-ttu-id="7c9ce-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7c9ce-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c9ce-116">See also</span></span>

- [<span data-ttu-id="7c9ce-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="7c9ce-117">Metadata Enumerations</span></span>](metadata-enumerations.md)
