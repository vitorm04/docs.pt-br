---
title: 'Método IXCLRDataProcess:: EndEnumModules'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9a7a23e53f5c2bc7d643046830cf335fec780f11
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420827"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="2bb47-102">Método IXCLRDataProcess:: EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="2bb47-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="2bb47-103">Libera os recursos usados por iteradores internos usados durante a enumeração do módulo.</span><span class="sxs-lookup"><span data-stu-id="2bb47-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2bb47-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bb47-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="2bb47-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2bb47-105">Parameters</span></span>

`handle`\
<span data-ttu-id="2bb47-106">fora Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="2bb47-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="2bb47-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2bb47-107">Remarks</span></span>

<span data-ttu-id="2bb47-108">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 26 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="2bb47-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2bb47-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2bb47-109">Requirements</span></span>

<span data-ttu-id="2bb47-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb47-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="2bb47-111">**Cabeçalho:** Nenhuma **biblioteca:** nenhuma **.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb47-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2bb47-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="2bb47-112">See also</span></span>

- [<span data-ttu-id="2bb47-113">Depuração</span><span class="sxs-lookup"><span data-stu-id="2bb47-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="2bb47-114">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="2bb47-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
