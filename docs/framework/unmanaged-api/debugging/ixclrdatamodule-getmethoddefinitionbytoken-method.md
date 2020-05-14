---
title: 'Método IXCLRDataModule:: GetMethodDefinitionByToken'
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
ms.openlocfilehash: c70920205b27376d453bdd0a13223c6a5569075b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395289"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="06ed0-102">Método IXCLRDataModule:: GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="06ed0-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="06ed0-103">Obtém a definição do método correspondente a um determinado token de metadados.</span><span class="sxs-lookup"><span data-stu-id="06ed0-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="06ed0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06ed0-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="06ed0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="06ed0-105">Parameters</span></span>

`token`\
<span data-ttu-id="06ed0-106">no O token do método.</span><span class="sxs-lookup"><span data-stu-id="06ed0-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="06ed0-107">fora A definição do método.</span><span class="sxs-lookup"><span data-stu-id="06ed0-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="06ed0-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="06ed0-108">Remarks</span></span>

<span data-ttu-id="06ed0-109">O método fornecido faz parte da `IXCLRDataModule` interface e corresponde ao slot 26 da tabela de métodos virtuais.</span><span class="sxs-lookup"><span data-stu-id="06ed0-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="06ed0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06ed0-110">Requirements</span></span>

<span data-ttu-id="06ed0-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06ed0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="06ed0-112">**Cabeçalho:** None</span><span class="sxs-lookup"><span data-stu-id="06ed0-112">**Header:** None</span></span>  
<span data-ttu-id="06ed0-113">**Biblioteca:** None</span><span class="sxs-lookup"><span data-stu-id="06ed0-113">**Library:** None</span></span>  
<span data-ttu-id="06ed0-114">**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="06ed0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="06ed0-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="06ed0-115">See also</span></span>

- [<span data-ttu-id="06ed0-116">Depuração</span><span class="sxs-lookup"><span data-stu-id="06ed0-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="06ed0-117">Interface IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="06ed0-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
