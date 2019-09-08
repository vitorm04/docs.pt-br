---
title: Interface IDefinitionAppId
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 929909a7f2c4fa1799c8fed94787b8f853c7eac2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796512"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="c91df-102">Interface IDefinitionAppId</span><span class="sxs-lookup"><span data-stu-id="c91df-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="c91df-103">Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="c91df-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c91df-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c91df-104">Methods</span></span>  
  
|<span data-ttu-id="c91df-105">Método</span><span class="sxs-lookup"><span data-stu-id="c91df-105">Method</span></span>|<span data-ttu-id="c91df-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c91df-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="c91df-107">Obtém uma cadeia de caracteres formatada que representa o código `IDefinitionAppId` neste objeto.</span><span class="sxs-lookup"><span data-stu-id="c91df-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="c91df-108">Define o código desse `IDefinitionAppId` objeto como o valor de cadeia de caracteres formatado especificado.</span><span class="sxs-lookup"><span data-stu-id="c91df-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="c91df-109">Obtém um ponteiro de interface para um objeto [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) que contém os assemblies no caminho do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="c91df-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="c91df-110">Define o caminho do aplicativo para o assembly no escopo atual como o valor referenciado pelo objeto [IDefinitionIdentity](idefinitionidentity-interface.md) especificado.</span><span class="sxs-lookup"><span data-stu-id="c91df-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="c91df-111">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma `IDefinitionAppId` assinatura para este objeto.</span><span class="sxs-lookup"><span data-stu-id="c91df-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="c91df-112">Define o identificador de token de uma assinatura para `IDefinitionAppId` esse objeto para o valor de cadeia de caracteres especificado.</span><span class="sxs-lookup"><span data-stu-id="c91df-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c91df-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c91df-113">Requirements</span></span>  
 <span data-ttu-id="c91df-114">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c91df-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c91df-115">**Cabeçalho:** Isolamento. h</span><span class="sxs-lookup"><span data-stu-id="c91df-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c91df-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c91df-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91df-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c91df-117">See also</span></span>

- [<span data-ttu-id="c91df-118">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="c91df-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
