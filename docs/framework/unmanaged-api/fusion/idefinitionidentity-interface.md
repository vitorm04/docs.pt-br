---
title: Interface IDefinitionIdentity
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb97c545d2d57ef589b5a7a5b3618eaa2b6f364f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686992"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="aefc0-102">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="aefc0-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="aefc0-103">Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="aefc0-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aefc0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="aefc0-104">Methods</span></span>  
  
|<span data-ttu-id="aefc0-105">Método</span><span class="sxs-lookup"><span data-stu-id="aefc0-105">Method</span></span>|<span data-ttu-id="aefc0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="aefc0-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="aefc0-107">Obtém um ponteiro de interface para um novo `IDefinitionIdentity` objeto que é idêntico a este `IDefinitionIdentity`, exceto para as alterações de atributo especificado.</span><span class="sxs-lookup"><span data-stu-id="aefc0-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="aefc0-108">Obtém um ponteiro de interface para um [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) que contém os atributos associados a este objeto `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="aefc0-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="aefc0-109">Obtém o valor do atributo com o nome especificado no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="aefc0-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="aefc0-110">Define o atributo que tem o nome especificado no namespace especificado para o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="aefc0-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aefc0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aefc0-111">Requirements</span></span>  
 <span data-ttu-id="aefc0-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aefc0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefc0-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="aefc0-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="aefc0-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aefc0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefc0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aefc0-115">See also</span></span>
- [<span data-ttu-id="aefc0-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="aefc0-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
