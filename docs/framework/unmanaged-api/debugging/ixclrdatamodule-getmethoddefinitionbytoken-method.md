---
title: IXCLRDataModule::GetMethodDefinitionByToken Method
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176663"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="9b838-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span><span class="sxs-lookup"><span data-stu-id="9b838-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="9b838-103">Obtém a definição do método correspondente a um determinado token de metadados.</span><span class="sxs-lookup"><span data-stu-id="9b838-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9b838-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b838-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="9b838-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b838-105">Parameters</span></span>

`token`\
<span data-ttu-id="9b838-106">[em] O token do método.</span><span class="sxs-lookup"><span data-stu-id="9b838-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="9b838-107">[fora] A definição do método.</span><span class="sxs-lookup"><span data-stu-id="9b838-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b838-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b838-108">Remarks</span></span>

<span data-ttu-id="9b838-109">O método fornecido faz `IXCLRDataModule` parte da interface e corresponde ao 25º slot da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="9b838-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9b838-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b838-110">Requirements</span></span>

<span data-ttu-id="9b838-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b838-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9b838-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="9b838-112">**Header:** None</span></span>  
<span data-ttu-id="9b838-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="9b838-113">**Library:** None</span></span>  
<span data-ttu-id="9b838-114">**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9b838-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9b838-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b838-115">See also</span></span>

- [<span data-ttu-id="9b838-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="9b838-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="9b838-117">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="9b838-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
