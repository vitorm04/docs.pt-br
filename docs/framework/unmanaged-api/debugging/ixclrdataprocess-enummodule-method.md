---
title: 'Método IXCLRDataProcess:: EnumModule'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420767"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="8d7df-102">Método IXCLRDataProcess:: EnumModule</span><span class="sxs-lookup"><span data-stu-id="8d7df-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="8d7df-103">Enumera os módulos desse processo.</span><span class="sxs-lookup"><span data-stu-id="8d7df-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8d7df-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d7df-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="8d7df-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d7df-105">Parameters</span></span>

`handle`\
<span data-ttu-id="8d7df-106">[entrada, saída] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="8d7df-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="8d7df-107">fora O módulo enumerado.</span><span class="sxs-lookup"><span data-stu-id="8d7df-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d7df-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d7df-108">Remarks</span></span>

<span data-ttu-id="8d7df-109">O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao 25º slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="8d7df-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d7df-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d7df-110">Requirements</span></span>

<span data-ttu-id="8d7df-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d7df-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8d7df-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="8d7df-112">**Header:** None</span></span>  
<span data-ttu-id="8d7df-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="8d7df-113">**Library:** None</span></span>  
<span data-ttu-id="8d7df-114">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8d7df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8d7df-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="8d7df-115">See also</span></span>

- [<span data-ttu-id="8d7df-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="8d7df-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="8d7df-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="8d7df-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="8d7df-118">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="8d7df-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="8d7df-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="8d7df-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
