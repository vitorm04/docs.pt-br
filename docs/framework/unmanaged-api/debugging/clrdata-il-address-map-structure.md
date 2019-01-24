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
ms.openlocfilehash: 3aac7e24fa9cd03350aebf5f441063bcedfaed04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644762"
---
# <a name="clrdatailaddressmap-structure"></a><span data-ttu-id="927d3-102">Estrutura CLRDATA_IL_ADDRESS_MAP</span><span class="sxs-lookup"><span data-stu-id="927d3-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="927d3-103">Define um IL para o mapeamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="927d3-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="927d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="927d3-104">Syntax</span></span>

```
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="927d3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="927d3-105">Members</span></span>

| <span data-ttu-id="927d3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="927d3-106">Member</span></span>         | <span data-ttu-id="927d3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="927d3-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="927d3-108">Deslocamento de IL para o intervalo de endereços independente</span><span class="sxs-lookup"><span data-stu-id="927d3-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="927d3-109">O endereço inicial do intervalo.</span><span class="sxs-lookup"><span data-stu-id="927d3-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="927d3-110">O endereço final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="927d3-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="927d3-111">O tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="927d3-111">The type of the data.</span></span> <span data-ttu-id="927d3-112">Esse valor não é usado atualmente</span><span class="sxs-lookup"><span data-stu-id="927d3-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="927d3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="927d3-113">Remarks</span></span>

<span data-ttu-id="927d3-114">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="927d3-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="927d3-115">Para usá-lo, definir a estrutura conforme especificado acima, onde `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="927d3-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="927d3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="927d3-116">Requirements</span></span>

<span data-ttu-id="927d3-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="927d3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="927d3-118">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="927d3-118">**Header:** None</span></span>  
<span data-ttu-id="927d3-119">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="927d3-119">**Library:** None</span></span>   
<span data-ttu-id="927d3-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="927d3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="927d3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="927d3-121">See also</span></span>

- [<span data-ttu-id="927d3-122">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="927d3-122">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="927d3-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="927d3-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="927d3-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="927d3-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
