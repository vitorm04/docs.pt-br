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
ms.openlocfilehash: d26cf45a0243d61757af5d9d0c00cf135ae15bdf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740858"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="96a3f-102">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="96a3f-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="96a3f-103">Fornece valores que são usados pela estrutura CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="96a3f-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="96a3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96a3f-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="96a3f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="96a3f-105">Members</span></span>

| <span data-ttu-id="96a3f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="96a3f-106">Member</span></span>                        | <span data-ttu-id="96a3f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a3f-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="96a3f-108">Para indicar que nada mais se aplica</span><span class="sxs-lookup"><span data-stu-id="96a3f-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="96a3f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="96a3f-109">Remarks</span></span>

<span data-ttu-id="96a3f-110">Esta enumeração reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="96a3f-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="96a3f-111">Para usá-lo, defina uma enumeração, conforme definido acima em seu código.</span><span class="sxs-lookup"><span data-stu-id="96a3f-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="96a3f-112">Isso também é um alias para `CLRDATA_ENUM` conforme mencionado na [tipos de dados comuns](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="96a3f-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="96a3f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96a3f-113">Requirements</span></span>

<span data-ttu-id="96a3f-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a3f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="96a3f-115">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="96a3f-115">**Header:** None</span></span>  
<span data-ttu-id="96a3f-116">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="96a3f-116">**Library:** None</span></span>  
<span data-ttu-id="96a3f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96a3f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="96a3f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96a3f-118">See also</span></span>

- [<span data-ttu-id="96a3f-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="96a3f-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="96a3f-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="96a3f-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
