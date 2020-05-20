---
title: 'Método IXCLRDataProcess:: EnumMethodInstanceByAddress'
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
ms.openlocfilehash: 142099ae5cf9637cc28e8c82aabcd831cc8f0f52
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420793"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="b062a-102">Método IXCLRDataProcess:: EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="b062a-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="b062a-103">Enumera as instâncias de método deste processo Iniciando em um deslocamento de endereço.</span><span class="sxs-lookup"><span data-stu-id="b062a-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b062a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b062a-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="b062a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b062a-105">Parameters</span></span>

`handle`\
<span data-ttu-id="b062a-106">no Um identificador para enumerar as instâncias de método.</span><span class="sxs-lookup"><span data-stu-id="b062a-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="b062a-107">fora A instância do método enumerado.</span><span class="sxs-lookup"><span data-stu-id="b062a-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="b062a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b062a-108">Remarks</span></span>

<span data-ttu-id="b062a-109">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot de 29 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="b062a-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b062a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b062a-110">Requirements</span></span>

<span data-ttu-id="b062a-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b062a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="b062a-112">**Cabeçalho:** Nenhuma **biblioteca:** nenhuma **.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b062a-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b062a-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="b062a-113">See also</span></span>

- [<span data-ttu-id="b062a-114">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="b062a-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b062a-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="b062a-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="b062a-116">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="b062a-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
