---
title: IXCLRDataProcess:EnumMethodMethodByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176650"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="27925-102">IXCLRDataProcess:EnumMethodMethodByAddress</span><span class="sxs-lookup"><span data-stu-id="27925-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="27925-103">Enumera as instâncias de método deste processo a partir de uma compensação de endereço.</span><span class="sxs-lookup"><span data-stu-id="27925-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="27925-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27925-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="27925-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="27925-105">Parameters</span></span>

`handle`\
<span data-ttu-id="27925-106">[em] Uma alça para enumerar as instâncias do método.</span><span class="sxs-lookup"><span data-stu-id="27925-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="27925-107">[fora] A instância do método enumerado.</span><span class="sxs-lookup"><span data-stu-id="27925-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="27925-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="27925-108">Remarks</span></span>

<span data-ttu-id="27925-109">O método fornecido faz `IXCLRDataProcess` parte da interface e corresponde ao 28º slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="27925-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="27925-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27925-110">Requirements</span></span>

<span data-ttu-id="27925-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27925-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="27925-112">**Cabeçalho:** Nenhuma **biblioteca:** Nenhuma **.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27925-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="27925-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="27925-113">See also</span></span>

- [<span data-ttu-id="27925-114">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="27925-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="27925-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="27925-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="27925-116">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="27925-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
