---
title: Estrutura DacpMethodDescData
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: cc54664ea8ad61005de3f3fae7407946d1c861b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793839"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="33c71-102">Estrutura DacpMethodDescData</span><span class="sxs-lookup"><span data-stu-id="33c71-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="33c71-103">Define um buffer de transporte para as informações de tempo de execução de um método.</span><span class="sxs-lookup"><span data-stu-id="33c71-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="33c71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="33c71-104">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="33c71-105">Membros</span><span class="sxs-lookup"><span data-stu-id="33c71-105">Members</span></span>

| <span data-ttu-id="33c71-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="33c71-106">Member</span></span>                       | <span data-ttu-id="33c71-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="33c71-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="33c71-108">Indica se o tempo de execução tem código nativo disponível para a instanciação fornecida do método.</span><span class="sxs-lookup"><span data-stu-id="33c71-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="33c71-109">Indica se o método é gerado dinamicamente por meio da geração de código leve.</span><span class="sxs-lookup"><span data-stu-id="33c71-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="33c71-110">O número do slot do método na tabela de métodos.</span><span class="sxs-lookup"><span data-stu-id="33c71-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="33c71-111">O endereço nativo inicial do método.</span><span class="sxs-lookup"><span data-stu-id="33c71-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="33c71-112">Ponteiro para um buffer usado internamente pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33c71-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="33c71-113">Ponteiro para a `MethodDesc` no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33c71-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="33c71-114">Ponteiro para um buffer usado internamente pelo tempo de execução para controlar métodos.</span><span class="sxs-lookup"><span data-stu-id="33c71-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="33c71-115">Ponteiro para um buffer usado internamente pelo tempo de execução para obter informações sobre o módulo.</span><span class="sxs-lookup"><span data-stu-id="33c71-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="33c71-116">Token associado ao método fornecido.</span><span class="sxs-lookup"><span data-stu-id="33c71-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="33c71-117">Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33c71-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="33c71-118">Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33c71-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="33c71-119">Se o método for dinâmico, o tempo de execução usará esse buffer internamente para o controle de informações.</span><span class="sxs-lookup"><span data-stu-id="33c71-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="33c71-120">Usado para popular a estrutura por solicitação quando um endereço de código nativo é fornecido.</span><span class="sxs-lookup"><span data-stu-id="33c71-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="33c71-121">Informações sobre a versão instrumentada mais recente do método.</span><span class="sxs-lookup"><span data-stu-id="33c71-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="33c71-122">Informações de ReJIT para o endereço nativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="33c71-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="33c71-123">Número de vezes que o método foi rejitted por meio de instrumentação.</span><span class="sxs-lookup"><span data-stu-id="33c71-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="33c71-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="33c71-124">Remarks</span></span>

<span data-ttu-id="33c71-125">Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="33c71-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="33c71-126">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="33c71-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="33c71-127">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="33c71-127">Requirements</span></span>
<span data-ttu-id="33c71-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33c71-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="33c71-129">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="33c71-129">**Header:** None</span></span>  
<span data-ttu-id="33c71-130">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="33c71-130">**Library:** None</span></span>  
<span data-ttu-id="33c71-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="33c71-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="33c71-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="33c71-132">See also</span></span>

- [<span data-ttu-id="33c71-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="33c71-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="33c71-134">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="33c71-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="33c71-135">Tipos de dados comuns</span><span class="sxs-lookup"><span data-stu-id="33c71-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
