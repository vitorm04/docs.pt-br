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
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108034"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="bae07-102">Interface IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="bae07-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="bae07-103">Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="bae07-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bae07-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bae07-104">Methods</span></span>  
  
|<span data-ttu-id="bae07-105">Método</span><span class="sxs-lookup"><span data-stu-id="bae07-105">Method</span></span>|<span data-ttu-id="bae07-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bae07-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="bae07-107">Obtém um ponteiro de interface para um novo objeto `IDefinitionIdentity` que é idêntico a este `IDefinitionIdentity`, exceto para as alterações de atributo especificadas.</span><span class="sxs-lookup"><span data-stu-id="bae07-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="bae07-108">Obtém um ponteiro de interface para um objeto [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) que contém os atributos associados a esse `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bae07-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="bae07-109">Obtém o valor do atributo com o nome especificado no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="bae07-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="bae07-110">Define o atributo que tem o nome especificado no namespace especificado para o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="bae07-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bae07-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bae07-111">Requirements</span></span>  
 <span data-ttu-id="bae07-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bae07-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bae07-113">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="bae07-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bae07-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bae07-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae07-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bae07-115">See also</span></span>

- [<span data-ttu-id="bae07-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="bae07-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
