---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976892"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="41f9b-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="41f9b-102">PeerSecuritySettings</span></span>
<span data-ttu-id="41f9b-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="41f9b-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f9b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41f9b-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="41f9b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="41f9b-105">Methods</span></span>  
 <span data-ttu-id="41f9b-106">A classe PeerSecuritySettings não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="41f9b-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="41f9b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="41f9b-107">Properties</span></span>  
 <span data-ttu-id="41f9b-108">A classe PeerSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="41f9b-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="41f9b-109">Modo</span><span class="sxs-lookup"><span data-stu-id="41f9b-109">Mode</span></span>  
 <span data-ttu-id="41f9b-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="41f9b-110">Data type: string</span></span>  
  
 <span data-ttu-id="41f9b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="41f9b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41f9b-112">Se no nível da mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.</span><span class="sxs-lookup"><span data-stu-id="41f9b-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="41f9b-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="41f9b-113">Transport</span></span>  
 <span data-ttu-id="41f9b-114">Tipo de dados: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="41f9b-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="41f9b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="41f9b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41f9b-116">Configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="41f9b-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f9b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41f9b-117">Requirements</span></span>  
  
|<span data-ttu-id="41f9b-118">MOF</span><span class="sxs-lookup"><span data-stu-id="41f9b-118">MOF</span></span>|<span data-ttu-id="41f9b-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="41f9b-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="41f9b-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="41f9b-120">Namespace</span></span>|<span data-ttu-id="41f9b-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="41f9b-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41f9b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41f9b-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
