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
ms.openlocfilehash: 3f22752446413c622a20340541b0ac328f63c77b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416312"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="8daaa-102">Método ISOSDacInterface::GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="8daaa-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="8daaa-103">Obtém os dados para o determinado [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8daaa-103">Gets the data for the given [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8daaa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8daaa-104">Syntax</span></span>

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a><span data-ttu-id="8daaa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8daaa-105">Parameters</span></span>

<span data-ttu-id="8daaa-106">`methodDesc` [in] O endereço do MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="8daaa-106">`methodDesc` [in] The address of the MethodDesc.</span></span>

<span data-ttu-id="8daaa-107">`ip` [in] O endereço IP do método.</span><span class="sxs-lookup"><span data-stu-id="8daaa-107">`ip` [in] The IP address of the method.</span></span>

<span data-ttu-id="8daaa-108">`data` [out] Os dados associados a MethodDesc conforme retornado pelo APIs internas.</span><span class="sxs-lookup"><span data-stu-id="8daaa-108">`data` [out] The data associated with the MethodDesc as returned from the internal APIs.</span></span> <span data-ttu-id="8daaa-109">A estrutura precisa de pelo menos bytes 168.</span><span class="sxs-lookup"><span data-stu-id="8daaa-109">The structure needs at least 168 bytes.</span></span>

<span data-ttu-id="8daaa-110">`cRevertedRejitVersions` [out] O número de versões do rejit revertido.</span><span class="sxs-lookup"><span data-stu-id="8daaa-110">`cRevertedRejitVersions` [out] The number of reverted rejit versions.</span></span>

<span data-ttu-id="8daaa-111">`rgRevertedRejitData` [out] Os dados associados com as versões do rejit revertido como retornado pelo APIs internas.</span><span class="sxs-lookup"><span data-stu-id="8daaa-111">`rgRevertedRejitData` [out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span> <span data-ttu-id="8daaa-112">A estrutura precisa de pelo menos 24 bytes.</span><span class="sxs-lookup"><span data-stu-id="8daaa-112">The structure needs at least 24 bytes.</span></span>

<span data-ttu-id="8daaa-113">`pcNeededRevertedRejitData` [out] O número de bytes necessários para armazenar os dados associados com as versões do ReJit revertidas.</span><span class="sxs-lookup"><span data-stu-id="8daaa-113">`pcNeededRevertedRejitData` [out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="8daaa-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8daaa-114">Remarks</span></span>

<span data-ttu-id="8daaa-115">O método fornecido é parte do `ISOSDacInterface` de interface e corresponde ao slot de 20 anos da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="8daaa-115">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="8daaa-116">Também o `CLRDATA_ADDRESS` são inteiro sem sinal de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8daaa-116">Also the `CLRDATA_ADDRESS` are 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="8daaa-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8daaa-117">Requirements</span></span>

<span data-ttu-id="8daaa-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8daaa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8daaa-119">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="8daaa-119">**Header:** None</span></span>  
<span data-ttu-id="8daaa-120">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="8daaa-120">**Library:** None</span></span>  
<span data-ttu-id="8daaa-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8daaa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8daaa-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8daaa-122">See Also</span></span>

- [<span data-ttu-id="8daaa-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="8daaa-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="8daaa-124">ISOSDacInterface Interface</span><span class="sxs-lookup"><span data-stu-id="8daaa-124">ISOSDacInterface Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
