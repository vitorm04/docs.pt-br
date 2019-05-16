---
title: Método ISOSDacInterface::GetMethodDescData
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: cdbf662c664d6c87b2fa17bcb10d735b0f573dd2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632313"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="7f487-102">Método ISOSDacInterface::GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="7f487-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="7f487-103">Obtém os dados para o ponteiro de MethodDesc determinado.</span><span class="sxs-lookup"><span data-stu-id="7f487-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7f487-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f487-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="7f487-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f487-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="7f487-106">[in] O endereço do MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="7f487-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="7f487-107">[in] O endereço IP do método.</span><span class="sxs-lookup"><span data-stu-id="7f487-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="7f487-108">[out] Os dados associados a MethodDesc conforme retornado pelo APIs internas.</span><span class="sxs-lookup"><span data-stu-id="7f487-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="7f487-109">[out] O número de versões do rejit revertido.</span><span class="sxs-lookup"><span data-stu-id="7f487-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="7f487-110">[out] Os dados associados com as versões do rejit revertido como retornado pelo APIs internas.</span><span class="sxs-lookup"><span data-stu-id="7f487-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="7f487-111">[out] O número de bytes necessários para armazenar os dados associados com as versões do ReJit revertidas.</span><span class="sxs-lookup"><span data-stu-id="7f487-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f487-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f487-112">Remarks</span></span>

<span data-ttu-id="7f487-113">O método fornecido é parte do `ISOSDacInterface` de interface e corresponde ao slot de 20 anos da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="7f487-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="7f487-114">Para poder usá-los [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) deve ser definido como um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7f487-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f487-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f487-115">Requirements</span></span>

<span data-ttu-id="7f487-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f487-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7f487-117">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7f487-117">**Header:** None</span></span>  
<span data-ttu-id="7f487-118">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="7f487-118">**Library:** None</span></span>  
<span data-ttu-id="7f487-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7f487-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7f487-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f487-120">See also</span></span>

- [<span data-ttu-id="7f487-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="7f487-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="7f487-122">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="7f487-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
