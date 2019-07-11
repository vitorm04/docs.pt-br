---
title: Método IXCLRDataProcess::EnumModule
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
ms.openlocfilehash: 40ab90a3218d4309cda709004a191e9440fe505d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769578"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="58884-102">Método IXCLRDataProcess::EnumModule</span><span class="sxs-lookup"><span data-stu-id="58884-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="58884-103">Enumera os módulos deste processo.</span><span class="sxs-lookup"><span data-stu-id="58884-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="58884-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58884-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="58884-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="58884-105">Parameters</span></span>

`handle`\
<span data-ttu-id="58884-106">[no, out] Um identificador para enumerar os módulos.</span><span class="sxs-lookup"><span data-stu-id="58884-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="58884-107">[out] O módulo enumerado.</span><span class="sxs-lookup"><span data-stu-id="58884-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="58884-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="58884-108">Remarks</span></span>

<span data-ttu-id="58884-109">O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde a 25 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="58884-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="58884-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="58884-110">Requirements</span></span>

<span data-ttu-id="58884-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58884-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="58884-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="58884-112">**Header:** None</span></span>  
<span data-ttu-id="58884-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="58884-113">**Library:** None</span></span>  
<span data-ttu-id="58884-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="58884-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="58884-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58884-115">See also</span></span>

- [<span data-ttu-id="58884-116">Enumeração CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="58884-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="58884-117">Depuração</span><span class="sxs-lookup"><span data-stu-id="58884-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="58884-118">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="58884-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="58884-119">Interface IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="58884-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
