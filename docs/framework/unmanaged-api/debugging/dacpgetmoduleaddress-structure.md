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
ms.openlocfilehash: cbea6c0562c68ae5d18247dc97bc53eb9dfbfd7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965917"
---
# <a name="dacpgetmoduleaddress-structure"></a><span data-ttu-id="c9aae-102">Estrutura DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="c9aae-102">DacpGetModuleAddress Structure</span></span>

<span data-ttu-id="c9aae-103">Define o contêiner para uma solicitação de endereço do módulo.</span><span class="sxs-lookup"><span data-stu-id="c9aae-103">Defines the container for a module address request.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c9aae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9aae-104">Syntax</span></span>

```
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a><span data-ttu-id="c9aae-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c9aae-105">Members</span></span>

| <span data-ttu-id="c9aae-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c9aae-106">Member</span></span>      | <span data-ttu-id="c9aae-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9aae-107">Description</span></span>                |
| ----------- | -------------------------- |
| `ModulePtr` | <span data-ttu-id="c9aae-108">O ponteiro para o módulo.</span><span class="sxs-lookup"><span data-stu-id="c9aae-108">The pointer to the module.</span></span> |

## <a name="methods"></a><span data-ttu-id="c9aae-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="c9aae-109">Methods</span></span>

| <span data-ttu-id="c9aae-110">Método</span><span class="sxs-lookup"><span data-stu-id="c9aae-110">Method</span></span>                                                                                               | <span data-ttu-id="c9aae-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9aae-111">Description</span></span>                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [<span data-ttu-id="c9aae-112">Solicitação</span><span class="sxs-lookup"><span data-stu-id="c9aae-112">Request</span></span>](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-request-method.md) | <span data-ttu-id="c9aae-113">Executa uma solicitação para preencher a estrutura da estrutura de determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c9aae-113">Performs a request to populate the structure from the given runtime structure.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c9aae-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9aae-114">Remarks</span></span>

<span data-ttu-id="c9aae-115">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c9aae-115">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="c9aae-116">Para usá-lo, definir a estrutura conforme especificado acima, onde `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="c9aae-116">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="c9aae-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9aae-117">Requirements</span></span>
<span data-ttu-id="c9aae-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9aae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="c9aae-119">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="c9aae-119">**Header:** None</span></span>  
<span data-ttu-id="c9aae-120">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="c9aae-120">**Library:** None</span></span>  
<span data-ttu-id="c9aae-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c9aae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c9aae-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9aae-122">See also</span></span>

- [<span data-ttu-id="c9aae-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="c9aae-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c9aae-124">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="c9aae-124">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
