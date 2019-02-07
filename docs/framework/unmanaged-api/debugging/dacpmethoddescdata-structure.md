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
ms.openlocfilehash: e9037fc035693e079e2471ad37263108656b8c01
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828576"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="d79ba-102">Estrutura DacpMethodDescData</span><span class="sxs-lookup"><span data-stu-id="d79ba-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="d79ba-103">Define um buffer de transporte para obter informações de tempo de execução do método.</span><span class="sxs-lookup"><span data-stu-id="d79ba-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d79ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d79ba-104">Syntax</span></span>

```
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

## <a name="members"></a><span data-ttu-id="d79ba-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d79ba-105">Members</span></span>

| <span data-ttu-id="d79ba-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d79ba-106">Member</span></span>                       | <span data-ttu-id="d79ba-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d79ba-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="d79ba-108">Indica se o tempo de execução tem disponível para a determinada instanciação do método de código nativo.</span><span class="sxs-lookup"><span data-stu-id="d79ba-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="d79ba-109">Indica se o método é gerado dinamicamente por meio da geração de código leve.</span><span class="sxs-lookup"><span data-stu-id="d79ba-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="d79ba-110">Número de slot do método na tabela de método.</span><span class="sxs-lookup"><span data-stu-id="d79ba-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="d79ba-111">Endereço de nativo inicial do método.</span><span class="sxs-lookup"><span data-stu-id="d79ba-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="d79ba-112">Ponteiro para um buffer usado internamente pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d79ba-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="d79ba-113">Ponteiro para o `MethodDesc` no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d79ba-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="d79ba-114">Ponteiro para um buffer usado internamente pelo tempo de execução para acompanhar os métodos.</span><span class="sxs-lookup"><span data-stu-id="d79ba-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="d79ba-115">Ponteiro para um buffer usado internamente pelo tempo de execução para obter informações de módulo.</span><span class="sxs-lookup"><span data-stu-id="d79ba-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="d79ba-116">Token associado com o método em questão.</span><span class="sxs-lookup"><span data-stu-id="d79ba-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="d79ba-117">Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d79ba-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="d79ba-118">Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d79ba-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="d79ba-119">Se o método for dinâmico, o tempo de execução usa esse buffer internamente para obter informações de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="d79ba-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="d79ba-120">Usado para preencher a estrutura por solicitação quando é fornecido um endereço de código nativo.</span><span class="sxs-lookup"><span data-stu-id="d79ba-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="d79ba-121">Informações sobre a versão mais recente do método instrumentada.</span><span class="sxs-lookup"><span data-stu-id="d79ba-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="d79ba-122">Informações do Rejit para o endereço nativo solicitado.</span><span class="sxs-lookup"><span data-stu-id="d79ba-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="d79ba-123">Número de vezes que o método foi rejitted por meio da instrumentação.</span><span class="sxs-lookup"><span data-stu-id="d79ba-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |


## <a name="remarks"></a><span data-ttu-id="d79ba-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="d79ba-124">Remarks</span></span>

<span data-ttu-id="d79ba-125">Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d79ba-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d79ba-126">Para usá-lo, defina a estrutura conforme especificado acima.</span><span class="sxs-lookup"><span data-stu-id="d79ba-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="d79ba-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d79ba-127">Requirements</span></span>
<span data-ttu-id="d79ba-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d79ba-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d79ba-129">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="d79ba-129">**Header:** None</span></span>  
<span data-ttu-id="d79ba-130">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="d79ba-130">**Library:** None</span></span>  
<span data-ttu-id="d79ba-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d79ba-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d79ba-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d79ba-132">See also</span></span>
- [<span data-ttu-id="d79ba-133">Depuração</span><span class="sxs-lookup"><span data-stu-id="d79ba-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="d79ba-134">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="d79ba-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d79ba-135">Tipos de dados comuns</span><span class="sxs-lookup"><span data-stu-id="d79ba-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
