---
title: 'Método ISOSDacInterface:: GetMethodDescData'
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
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396942"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="19d4c-102">Método ISOSDacInterface:: GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="19d4c-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="19d4c-103">Obtém os dados para o ponteiro MethodDesc fornecido.</span><span class="sxs-lookup"><span data-stu-id="19d4c-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="19d4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="19d4c-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="19d4c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="19d4c-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="19d4c-106">no O endereço do MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="19d4c-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="19d4c-107">no O endereço IP do método.</span><span class="sxs-lookup"><span data-stu-id="19d4c-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="19d4c-108">fora Os dados associados ao MethodDesc como retornados das APIs internas.</span><span class="sxs-lookup"><span data-stu-id="19d4c-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="19d4c-109">fora O número de versões de ReJIT revertidas.</span><span class="sxs-lookup"><span data-stu-id="19d4c-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="19d4c-110">fora Os dados associados às versões de ReJIT revertidas, conforme retornado das APIs internas.</span><span class="sxs-lookup"><span data-stu-id="19d4c-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="19d4c-111">fora O número de bytes necessários para armazenar os dados associados às versões de ReJit revertidas.</span><span class="sxs-lookup"><span data-stu-id="19d4c-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="19d4c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="19d4c-112">Remarks</span></span>

<span data-ttu-id="19d4c-113">O método fornecido faz parte da `ISOSDacInterface` interface e corresponde ao slot 21 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="19d4c-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="19d4c-114">Para poder usá-los, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) deve ser definido como um inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="19d4c-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="19d4c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="19d4c-115">Requirements</span></span>

<span data-ttu-id="19d4c-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d4c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="19d4c-117">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="19d4c-117">**Header:** None</span></span>  
<span data-ttu-id="19d4c-118">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="19d4c-118">**Library:** None</span></span>  
<span data-ttu-id="19d4c-119">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="19d4c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="19d4c-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="19d4c-120">See also</span></span>

- [<span data-ttu-id="19d4c-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="19d4c-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="19d4c-122">Interface ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="19d4c-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
