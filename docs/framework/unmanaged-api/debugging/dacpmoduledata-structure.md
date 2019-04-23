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
ms.openlocfilehash: 752d87c5f4a6b8d854a06be8962ee754cdd4622d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131996"
---
# <a name="dacpmoduledata-structure"></a><span data-ttu-id="2ffde-102">Estrutura DacpModuleData</span><span class="sxs-lookup"><span data-stu-id="2ffde-102">DacpModuleData Structure</span></span>

<span data-ttu-id="2ffde-103">Define um buffer de transporte para obter informações de tempo de execução de um módulo.</span><span class="sxs-lookup"><span data-stu-id="2ffde-103">Defines a transport buffer for a module's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2ffde-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ffde-104">Syntax</span></span>

```
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File; 
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a><span data-ttu-id="2ffde-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2ffde-105">Members</span></span>

| <span data-ttu-id="2ffde-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2ffde-106">Member</span></span>    | <span data-ttu-id="2ffde-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ffde-107">Description</span></span>                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | <span data-ttu-id="2ffde-108">Endereço do objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="2ffde-108">Address of the module object.</span></span>                                           |
| `File`    | <span data-ttu-id="2ffde-109">Um ponteiro para o arquivo executável portátil (PE).</span><span class="sxs-lookup"><span data-stu-id="2ffde-109">A pointer to the portable executable (PE) file.</span></span>                       |
| `ilBase`  | <span data-ttu-id="2ffde-110">Base do endereço da imagem carregada.</span><span class="sxs-lookup"><span data-stu-id="2ffde-110">The address of the loaded image's base.</span></span>                                 |
| `payLoad` | <span data-ttu-id="2ffde-111">Um buffer de carga para obter informações adicionais de módulo usados pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2ffde-111">A payload buffer for additional module information used by the runtime.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2ffde-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ffde-112">Remarks</span></span>

<span data-ttu-id="2ffde-113">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2ffde-113">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="2ffde-114">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="2ffde-114">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ffde-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ffde-115">Requirements</span></span>
<span data-ttu-id="2ffde-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ffde-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2ffde-117">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="2ffde-117">**Header:** None</span></span>  
<span data-ttu-id="2ffde-118">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="2ffde-118">**Library:** None</span></span>  
<span data-ttu-id="2ffde-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2ffde-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2ffde-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ffde-120">See also</span></span>

- [<span data-ttu-id="2ffde-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="2ffde-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2ffde-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="2ffde-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
