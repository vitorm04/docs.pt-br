---
title: Interface IAssemblyName
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134325"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="f9eac-102">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f9eac-102">IAssemblyName Interface</span></span>
<span data-ttu-id="f9eac-103">Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.</span><span class="sxs-lookup"><span data-stu-id="f9eac-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9eac-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f9eac-104">Methods</span></span>  
  
|<span data-ttu-id="f9eac-105">Método</span><span class="sxs-lookup"><span data-stu-id="f9eac-105">Method</span></span>|<span data-ttu-id="f9eac-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9eac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9eac-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="f9eac-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="f9eac-108">Cria uma cópia superficial deste `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="f9eac-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f9eac-109">Método Finalize</span><span class="sxs-lookup"><span data-stu-id="f9eac-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="f9eac-110">Permite que este `IAssemblyName` objeto libere recursos e execute outras operações de limpeza antes que seu destruidor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="f9eac-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="f9eac-111">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="f9eac-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="f9eac-112">Obtém o nome legível do assembly referenciado por este `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="f9eac-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f9eac-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="f9eac-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="f9eac-114">Obtém o nome simples e não criptografado do assembly referenciado por este `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="f9eac-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f9eac-115">Método GetProperty</span><span class="sxs-lookup"><span data-stu-id="f9eac-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="f9eac-116">Obtém um ponteiro para a propriedade referenciada pelo `PropertyId`especificado.</span><span class="sxs-lookup"><span data-stu-id="f9eac-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="f9eac-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="f9eac-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="f9eac-118">Obtém as informações de versão para o assembly referenciado por este objeto de `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f9eac-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="f9eac-119">Método IsEqual</span><span class="sxs-lookup"><span data-stu-id="f9eac-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="f9eac-120">Determina se um objeto de `IAssemblyName` especificado é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificados.</span><span class="sxs-lookup"><span data-stu-id="f9eac-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="f9eac-121">Método SetProperty</span><span class="sxs-lookup"><span data-stu-id="f9eac-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="f9eac-122">Define o valor da propriedade referenciada pelo `PropertyId`especificado.</span><span class="sxs-lookup"><span data-stu-id="f9eac-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9eac-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9eac-123">Requirements</span></span>  
 <span data-ttu-id="f9eac-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9eac-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9eac-125">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f9eac-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f9eac-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9eac-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9eac-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9eac-127">See also</span></span>

- [<span data-ttu-id="f9eac-128">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="f9eac-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="f9eac-129">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="f9eac-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
