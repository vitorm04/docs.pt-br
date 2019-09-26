---
title: Enumeração CLRDataSourceType
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274104"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="9605b-102">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="9605b-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="9605b-103">Fornece valores que são usados pela estrutura CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="9605b-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9605b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9605b-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="9605b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9605b-105">Members</span></span>

| <span data-ttu-id="9605b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9605b-106">Member</span></span>                        | <span data-ttu-id="9605b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9605b-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="9605b-108">Para indicar que nada mais se aplica</span><span class="sxs-lookup"><span data-stu-id="9605b-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="9605b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9605b-109">Remarks</span></span>

<span data-ttu-id="9605b-110">Essa enumeração reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9605b-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="9605b-111">Para usá-lo, defina uma enumeração conforme definido acima no seu código.</span><span class="sxs-lookup"><span data-stu-id="9605b-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="9605b-112">Isso também é alias `CLRDATA_ENUM` como mencionado em tipos de [dados comuns](../common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9605b-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9605b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9605b-113">Requirements</span></span>

<span data-ttu-id="9605b-114">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9605b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9605b-115">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="9605b-115">**Header:** None</span></span>  
<span data-ttu-id="9605b-116">**Biblioteca** Nenhum</span><span class="sxs-lookup"><span data-stu-id="9605b-116">**Library:** None</span></span>  
<span data-ttu-id="9605b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9605b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9605b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9605b-118">See also</span></span>

- [<span data-ttu-id="9605b-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="9605b-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="9605b-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="9605b-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
