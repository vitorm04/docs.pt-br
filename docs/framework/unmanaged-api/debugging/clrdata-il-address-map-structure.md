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
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179372"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="c571f-102">Estrutura CLRDATA_IL_ADDRESS_MAP</span><span class="sxs-lookup"><span data-stu-id="c571f-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="c571f-103">Define um IL para endereçar mapeamento.</span><span class="sxs-lookup"><span data-stu-id="c571f-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c571f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c571f-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="c571f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c571f-105">Members</span></span>

| <span data-ttu-id="c571f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c571f-106">Member</span></span>         | <span data-ttu-id="c571f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c571f-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="c571f-108">Deslocamento il para a faixa de endereço contida</span><span class="sxs-lookup"><span data-stu-id="c571f-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="c571f-109">O endereço inicial do intervalo.</span><span class="sxs-lookup"><span data-stu-id="c571f-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="c571f-110">O endereço final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="c571f-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="c571f-111">O tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="c571f-111">The type of the data.</span></span> <span data-ttu-id="c571f-112">Este valor não é usado no momento</span><span class="sxs-lookup"><span data-stu-id="c571f-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="c571f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c571f-113">Remarks</span></span>

<span data-ttu-id="c571f-114">Esta estrutura vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c571f-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c571f-115">Para usá-lo, defina a estrutura `CLRDATA_ADDRESS` como especificado acima, onde está um inteiro não assinado de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c571f-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="c571f-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c571f-116">Requirements</span></span>

<span data-ttu-id="c571f-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c571f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c571f-118">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="c571f-118">**Header:** None</span></span>  
<span data-ttu-id="c571f-119">**Biblioteca:** Nenhuma **versão framework .NET:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c571f-119">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c571f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="c571f-120">See also</span></span>

- [<span data-ttu-id="c571f-121">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="c571f-121">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="c571f-122">Depuração</span><span class="sxs-lookup"><span data-stu-id="c571f-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="c571f-123">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="c571f-123">Debugging Structures</span></span>](debugging-structures.md)
