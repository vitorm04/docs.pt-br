---
title: Estrutura CLRDATA_IL_ADDRESS_MAP
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274288"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="96d1c-102">Estrutura CLRDATA_IL_ADDRESS_MAP</span><span class="sxs-lookup"><span data-stu-id="96d1c-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="96d1c-103">Define um IL para o mapeamento de endereços.</span><span class="sxs-lookup"><span data-stu-id="96d1c-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="96d1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96d1c-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="96d1c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="96d1c-105">Members</span></span>

| <span data-ttu-id="96d1c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="96d1c-106">Member</span></span>         | <span data-ttu-id="96d1c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="96d1c-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="96d1c-108">Deslocamento de IL para o intervalo de endereços contidos</span><span class="sxs-lookup"><span data-stu-id="96d1c-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="96d1c-109">O endereço inicial do intervalo.</span><span class="sxs-lookup"><span data-stu-id="96d1c-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="96d1c-110">O endereço final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="96d1c-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="96d1c-111">O tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="96d1c-111">The type of the data.</span></span> <span data-ttu-id="96d1c-112">Este valor não está sendo usado no momento</span><span class="sxs-lookup"><span data-stu-id="96d1c-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="96d1c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="96d1c-113">Remarks</span></span>

<span data-ttu-id="96d1c-114">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="96d1c-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="96d1c-115">Para usá-lo, defina a estrutura conforme especificado acima, `CLRDATA_ADDRESS` em que é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="96d1c-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="96d1c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96d1c-116">Requirements</span></span>

<span data-ttu-id="96d1c-117">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96d1c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="96d1c-118">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="96d1c-118">**Header:** None</span></span>  
<span data-ttu-id="96d1c-119">**Biblioteca** Nenhum</span><span class="sxs-lookup"><span data-stu-id="96d1c-119">**Library:** None</span></span>   
<span data-ttu-id="96d1c-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96d1c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="96d1c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96d1c-121">See also</span></span>

- [<span data-ttu-id="96d1c-122">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="96d1c-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="96d1c-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="96d1c-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="96d1c-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="96d1c-124">Debugging Structures</span></span>](debugging-structures.md)
