---
title: 'Método ISOSDacInterface:: GetMethodDescPtrFromIP'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c3de9e5ffe23a13c126343c6f74f042bf1239609
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421001"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a><span data-ttu-id="db876-102">Método ISOSDacInterface:: GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="db876-102">ISOSDacInterface::GetMethodDescPtrFromIP Method</span></span>

<span data-ttu-id="db876-103">Recupera o ponteiro do MethodDesc correspondente ao método que contém o endereço de instrução nativo fornecido.</span><span class="sxs-lookup"><span data-stu-id="db876-103">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="db876-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db876-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a><span data-ttu-id="db876-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db876-105">Parameters</span></span>

`ip`\
<span data-ttu-id="db876-106">no Um endereço dentro do método em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="db876-106">[in] An address within the method at runtime.</span></span>

`ppMD`\
<span data-ttu-id="db876-107">fora O endereço do `MethodDesc` para o método específico.</span><span class="sxs-lookup"><span data-stu-id="db876-107">[out] The address of the `MethodDesc` for the particular method.</span></span>

## <a name="remarks"></a><span data-ttu-id="db876-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="db876-108">Remarks</span></span>

<span data-ttu-id="db876-109">O método fornecido faz parte da [ `ISOSDacInterface` interface](isosdacinterface-interface.md) e corresponde ao slot 22 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="db876-109">The provided method is part of the [`ISOSDacInterface` interface](isosdacinterface-interface.md) and corresponds to the 22nd slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="db876-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db876-110">Requirements</span></span>

<span data-ttu-id="db876-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db876-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="db876-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="db876-112">**Header:** None</span></span>  
<span data-ttu-id="db876-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="db876-113">**Library:** None</span></span>  
<span data-ttu-id="db876-114">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="db876-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="db876-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="db876-115">See also</span></span>

- [<span data-ttu-id="db876-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="db876-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="db876-117">Interface ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="db876-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
