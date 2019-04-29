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
ms.openlocfilehash: 727005437289b4bc66ab90f280b80a79f4db06db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775486"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="4765a-102">Método IXCLRDataModule::GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="4765a-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="4765a-103">Obtém a definição do método correspondente a um token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="4765a-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4765a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4765a-104">Syntax</span></span>

```
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="4765a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4765a-105">Parameters</span></span>

`token`\
<span data-ttu-id="4765a-106">[in] O token de método.</span><span class="sxs-lookup"><span data-stu-id="4765a-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="4765a-107">[out] A definição do método.</span><span class="sxs-lookup"><span data-stu-id="4765a-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="4765a-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4765a-108">Remarks</span></span>

<span data-ttu-id="4765a-109">O método fornecido é parte do `IXCLRDataModule` de interface e corresponde a 25 de slot da tabela de método virtual.</span><span class="sxs-lookup"><span data-stu-id="4765a-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4765a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4765a-110">Requirements</span></span>

<span data-ttu-id="4765a-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4765a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4765a-112">**Cabeçalho:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4765a-112">**Header:** None</span></span>  
<span data-ttu-id="4765a-113">**Biblioteca:** Nenhum</span><span class="sxs-lookup"><span data-stu-id="4765a-113">**Library:** None</span></span>  
<span data-ttu-id="4765a-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4765a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="4765a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4765a-115">See also</span></span>

- [<span data-ttu-id="4765a-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="4765a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="4765a-117">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="4765a-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
