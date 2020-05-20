---
title: 'Método IXCLRDataModule:: getversionid'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420858"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="bebb4-102">Método IXCLRDataModule:: getversionid</span><span class="sxs-lookup"><span data-stu-id="bebb4-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="bebb4-103">Obtém o identificador de versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="bebb4-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bebb4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bebb4-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="bebb4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bebb4-105">Parameters</span></span>

`vid`\
<span data-ttu-id="bebb4-106">fora O identificador de versão do módulo.</span><span class="sxs-lookup"><span data-stu-id="bebb4-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="bebb4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bebb4-107">Remarks</span></span>

<span data-ttu-id="bebb4-108">O método fornecido faz parte da `IXCLRDataModule` interface e corresponde ao slot 41 ª da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="bebb4-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bebb4-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bebb4-109">Requirements</span></span>

<span data-ttu-id="bebb4-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bebb4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bebb4-111">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="bebb4-111">**Header:** None</span></span>  
<span data-ttu-id="bebb4-112">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="bebb4-112">**Library:** None</span></span>  
<span data-ttu-id="bebb4-113">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bebb4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bebb4-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="bebb4-114">See also</span></span>

- [<span data-ttu-id="bebb4-115">Depuração</span><span class="sxs-lookup"><span data-stu-id="bebb4-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="bebb4-116">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="bebb4-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
