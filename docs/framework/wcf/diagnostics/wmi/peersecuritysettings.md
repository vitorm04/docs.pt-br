---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 92aca4c790607de91314aacf6414d0dfacea9a9f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193156"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="f688e-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f688e-102">PeerSecuritySettings</span></span>
<span data-ttu-id="f688e-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f688e-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f688e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f688e-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f688e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f688e-105">Methods</span></span>  
 <span data-ttu-id="f688e-106">A classe PeerSecuritySettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="f688e-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f688e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f688e-107">Properties</span></span>  
 <span data-ttu-id="f688e-108">A classe PeerSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f688e-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="f688e-109">Modo</span><span class="sxs-lookup"><span data-stu-id="f688e-109">Mode</span></span>  
 <span data-ttu-id="f688e-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f688e-110">Data type: string</span></span>  
  
 <span data-ttu-id="f688e-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f688e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f688e-112">Se no nível da mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.</span><span class="sxs-lookup"><span data-stu-id="f688e-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="f688e-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="f688e-113">Transport</span></span>  
 <span data-ttu-id="f688e-114">Tipo de dados: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f688e-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="f688e-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f688e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f688e-116">Configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="f688e-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f688e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f688e-117">Requirements</span></span>  
  
|<span data-ttu-id="f688e-118">MOF</span><span class="sxs-lookup"><span data-stu-id="f688e-118">MOF</span></span>|<span data-ttu-id="f688e-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f688e-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f688e-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="f688e-120">Namespace</span></span>|<span data-ttu-id="f688e-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f688e-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f688e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f688e-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
