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
ms.openlocfilehash: 401c23e44cc473d0a27a82a00343852693cb0f2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429339"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="5e950-102">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="5e950-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="5e950-103">Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="5e950-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e950-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="5e950-104">Methods</span></span>  
  
|<span data-ttu-id="5e950-105">Método</span><span class="sxs-lookup"><span data-stu-id="5e950-105">Method</span></span>|<span data-ttu-id="5e950-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e950-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="5e950-107">Obtém um ponteiro de interface para um novo `IDefinitionIdentity` objeto que é idêntico a esta `IDefinitionIdentity`, exceto para as alterações de atributo especificado.</span><span class="sxs-lookup"><span data-stu-id="5e950-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="5e950-108">Obtém um ponteiro de interface para um [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) objeto que contém os atributos associados a este `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5e950-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="5e950-109">Obtém o valor do atributo com o nome especificado no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="5e950-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="5e950-110">Define o atributo que tem o nome especificado no namespace especificado para o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="5e950-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e950-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e950-111">Requirements</span></span>  
 <span data-ttu-id="5e950-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e950-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e950-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="5e950-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5e950-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e950-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e950-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e950-115">See Also</span></span>  
 [<span data-ttu-id="5e950-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="5e950-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
