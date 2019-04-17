---
title: Método IXCLRDataProcess::EndEnumModules
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
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611426"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="edaa1-102">Método IXCLRDataProcess::EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="edaa1-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="edaa1-103">Libera os recursos usados pelos iteradores internos usados durante a enumeração de módulo.</span><span class="sxs-lookup"><span data-stu-id="edaa1-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="edaa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="edaa1-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="edaa1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="edaa1-105">Parameters</span></span>

`handle`\
<span data-ttu-id="edaa1-106">[out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="edaa1-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="edaa1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="edaa1-107">Remarks</span></span>

<span data-ttu-id="edaa1-108">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 26 da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="edaa1-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="edaa1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="edaa1-109">Requirements</span></span>

<span data-ttu-id="edaa1-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edaa1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="edaa1-111">**Cabeçalho:** Nenhum **biblioteca:** Nenhum **versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="edaa1-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="edaa1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edaa1-112">See also</span></span>

- [<span data-ttu-id="edaa1-113">Depuração</span><span class="sxs-lookup"><span data-stu-id="edaa1-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="edaa1-114">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="edaa1-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
