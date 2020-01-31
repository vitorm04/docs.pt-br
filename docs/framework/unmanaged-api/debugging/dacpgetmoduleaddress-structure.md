---
title: Estrutura DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789204"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="d94b4-102">Estrutura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="d94b4-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="d94b4-103">Define o contêiner para uma solicitação de endereço de módulo.</span><span class="sxs-lookup"><span data-stu-id="d94b4-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d94b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d94b4-104">Syntax</span></span>

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="d94b4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d94b4-105">Members</span></span>

| <span data-ttu-id="d94b4-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d94b4-106">Member</span></span>      | <span data-ttu-id="d94b4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d94b4-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="d94b4-108">O ponteiro para o módulo.</span><span class="sxs-lookup"><span data-stu-id="d94b4-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="d94b4-109">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d94b4-109">Methods</span></span>

| <span data-ttu-id="d94b4-110">Método</span><span class="sxs-lookup"><span data-stu-id="d94b4-110">Method</span></span>                                                                                               | <span data-ttu-id="d94b4-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d94b4-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="d94b4-112">Solicitação</span><span class="sxs-lookup"><span data-stu-id="d94b4-112">Request</span></span>](dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="d94b4-113">Executa uma solicitação para popular a estrutura da estrutura de tempo de execução fornecida.</span><span class="sxs-lookup"><span data-stu-id="d94b4-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d94b4-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="d94b4-114">Remarks</span></span>

<span data-ttu-id="d94b4-115">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d94b4-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d94b4-116">Para usá-lo, defina a estrutura conforme especificado acima, em que `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d94b4-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d94b4-117">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d94b4-117">Requirements</span></span>
<span data-ttu-id="d94b4-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d94b4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d94b4-119">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="d94b4-119">**Header:** None</span></span>  
<span data-ttu-id="d94b4-120">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="d94b4-120">**Library:** None</span></span>  
<span data-ttu-id="d94b4-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d94b4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d94b4-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="d94b4-122">See also</span></span>

- [<span data-ttu-id="d94b4-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="d94b4-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="d94b4-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="d94b4-124">Debugging Structures</span></span>](debugging-structures.md)
