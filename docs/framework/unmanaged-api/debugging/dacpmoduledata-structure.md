---
title: Estrutura DacpModuleData
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: e10d1792a8dc0b57ddd121ec09854e8e1824cade
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860806"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="5320d-102">Estrutura DacpModuleData</span><span class="sxs-lookup"><span data-stu-id="5320d-102">DacpModuleData Structure</span></span>

<span data-ttu-id="5320d-103">Define um buffer de transporte para as informações de tempo de execução de um módulo.</span><span class="sxs-lookup"><span data-stu-id="5320d-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5320d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5320d-104">Syntax</span></span>

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="5320d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5320d-105">Members</span></span>

| <span data-ttu-id="5320d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5320d-106">Member</span></span>    | <span data-ttu-id="5320d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5320d-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="5320d-108">Endereço do objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="5320d-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="5320d-109">Um ponteiro para o arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="5320d-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="5320d-110">O endereço da base da imagem carregada.</span><span class="sxs-lookup"><span data-stu-id="5320d-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="5320d-111">Um buffer de carga para informações adicionais do módulo usadas pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5320d-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="5320d-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="5320d-112">Remarks</span></span>

<span data-ttu-id="5320d-113">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="5320d-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="5320d-114">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="5320d-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="5320d-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5320d-115">Requirements</span></span>
<span data-ttu-id="5320d-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5320d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5320d-117">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="5320d-117">**Header:** None</span></span>  
<span data-ttu-id="5320d-118">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="5320d-118">**Library:** None</span></span>  
<span data-ttu-id="5320d-119">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5320d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5320d-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="5320d-120">See also</span></span>

- [<span data-ttu-id="5320d-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="5320d-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="5320d-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="5320d-122">Debugging Structures</span></span>](debugging-structures.md)
