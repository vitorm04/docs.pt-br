---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963001"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="298db-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="298db-102">PeerSecuritySettings</span></span>
<span data-ttu-id="298db-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="298db-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="298db-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="298db-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="298db-105">Methods</span></span>  
 <span data-ttu-id="298db-106">A classe PeerSecuritySettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="298db-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="298db-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="298db-107">Properties</span></span>  
 <span data-ttu-id="298db-108">A classe PeerSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="298db-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="298db-109">Modo</span><span class="sxs-lookup"><span data-stu-id="298db-109">Mode</span></span>  
 <span data-ttu-id="298db-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="298db-110">Data type: string</span></span>  
  
 <span data-ttu-id="298db-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="298db-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="298db-112">Se no nível da mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.</span><span class="sxs-lookup"><span data-stu-id="298db-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="298db-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="298db-113">Transport</span></span>  
 <span data-ttu-id="298db-114">Tipo de dados: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="298db-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="298db-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="298db-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="298db-116">Configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="298db-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="298db-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="298db-117">Requirements</span></span>  
  
|<span data-ttu-id="298db-118">MOF</span><span class="sxs-lookup"><span data-stu-id="298db-118">MOF</span></span>|<span data-ttu-id="298db-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="298db-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="298db-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="298db-120">Namespace</span></span>|<span data-ttu-id="298db-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="298db-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="298db-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="298db-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
