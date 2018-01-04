---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="94515-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="94515-102">PeerSecuritySettings</span></span>
<span data-ttu-id="94515-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="94515-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94515-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94515-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="94515-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="94515-105">Methods</span></span>  
 <span data-ttu-id="94515-106">A classe PeerSecuritySettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="94515-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="94515-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="94515-107">Properties</span></span>  
 <span data-ttu-id="94515-108">A classe PeerSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="94515-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="94515-109">Modo</span><span class="sxs-lookup"><span data-stu-id="94515-109">Mode</span></span>  
 <span data-ttu-id="94515-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="94515-110">Data type: string</span></span>  
  
 <span data-ttu-id="94515-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="94515-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94515-112">Se nível de mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.</span><span class="sxs-lookup"><span data-stu-id="94515-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="94515-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="94515-113">Transport</span></span>  
 <span data-ttu-id="94515-114">Tipo de dados: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="94515-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="94515-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="94515-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94515-116">Configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="94515-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94515-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94515-117">Requirements</span></span>  
  
|<span data-ttu-id="94515-118">MOF</span><span class="sxs-lookup"><span data-stu-id="94515-118">MOF</span></span>|<span data-ttu-id="94515-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="94515-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="94515-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="94515-120">Namespace</span></span>|<span data-ttu-id="94515-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="94515-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94515-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94515-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
