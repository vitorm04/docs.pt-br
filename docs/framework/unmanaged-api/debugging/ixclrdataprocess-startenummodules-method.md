---
title: 'Método IXCLRDataProcess:: StartEnumModules'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420715"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="94aab-102">Método IXCLRDataProcess:: StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="94aab-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="94aab-103">Fornece um identificador para enumerar os módulos de um processo.</span><span class="sxs-lookup"><span data-stu-id="94aab-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="94aab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94aab-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="94aab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94aab-105">Parameters</span></span>

`handle`\
<span data-ttu-id="94aab-106">fora Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="94aab-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="94aab-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="94aab-107">Remarks</span></span>

<span data-ttu-id="94aab-108">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 24 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="94aab-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="94aab-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94aab-109">Requirements</span></span>

<span data-ttu-id="94aab-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94aab-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="94aab-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="94aab-111">**Header:** None</span></span>  
<span data-ttu-id="94aab-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="94aab-112">**Library:** None</span></span>  
<span data-ttu-id="94aab-113">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94aab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="94aab-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="94aab-114">See also</span></span>

- [<span data-ttu-id="94aab-115">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="94aab-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="94aab-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="94aab-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="94aab-117">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="94aab-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
