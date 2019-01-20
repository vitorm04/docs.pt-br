---
title: Método IXCLRDataModule::GetMethodDefinitionByToken
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
ms.openlocfilehash: 27f1ee28aff95340d4b533473b2f699a9405c3a2
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416313"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="5ac08-102">Método IXCLRDataModule::GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="5ac08-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="5ac08-103">Obtém a definição do método correspondente a um token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="5ac08-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5ac08-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ac08-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

### <a name="parameters"></a><span data-ttu-id="5ac08-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ac08-105">Parameters</span></span>

<span data-ttu-id="5ac08-106">`token` [in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="5ac08-106">`token` [in] The method token.</span></span>

<span data-ttu-id="5ac08-107">`methodDefinition` [out] A definição do método.</span><span class="sxs-lookup"><span data-stu-id="5ac08-107">`methodDefinition` [out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ac08-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ac08-108">Remarks</span></span>

<span data-ttu-id="5ac08-109">O método fornecido é parte do `IXCLRDataModule` de interface e corresponde a 25 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="5ac08-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ac08-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ac08-110">Requirements</span></span>

<span data-ttu-id="5ac08-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac08-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5ac08-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="5ac08-112">**Header:** None</span></span>  
<span data-ttu-id="5ac08-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="5ac08-113">**Library:** None</span></span>  
<span data-ttu-id="5ac08-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac08-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="5ac08-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ac08-115">See Also</span></span>

- [<span data-ttu-id="5ac08-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="5ac08-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="5ac08-117">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="5ac08-117">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
