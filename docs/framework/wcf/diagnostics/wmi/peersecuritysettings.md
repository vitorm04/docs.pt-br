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
ms.openlocfilehash: 02cd483f2f7ec5e599b286b672d051a0e8d57940
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="af0b4-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="af0b4-102">PeerSecuritySettings</span></span>
<span data-ttu-id="af0b4-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="af0b4-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af0b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af0b4-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="af0b4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="af0b4-105">Methods</span></span>  
 <span data-ttu-id="af0b4-106">A classe PeerSecuritySettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="af0b4-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="af0b4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="af0b4-107">Properties</span></span>  
 <span data-ttu-id="af0b4-108">A classe PeerSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="af0b4-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="af0b4-109">Modo</span><span class="sxs-lookup"><span data-stu-id="af0b4-109">Mode</span></span>  
 <span data-ttu-id="af0b4-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="af0b4-110">Data type: string</span></span>  
  
 <span data-ttu-id="af0b4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="af0b4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af0b4-112">Se nível de mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.</span><span class="sxs-lookup"><span data-stu-id="af0b4-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="af0b4-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="af0b4-113">Transport</span></span>  
 <span data-ttu-id="af0b4-114">Tipo de dados: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="af0b4-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="af0b4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="af0b4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af0b4-116">Configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="af0b4-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af0b4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="af0b4-117">Requirements</span></span>  
  
|<span data-ttu-id="af0b4-118">MOF</span><span class="sxs-lookup"><span data-stu-id="af0b4-118">MOF</span></span>|<span data-ttu-id="af0b4-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="af0b4-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="af0b4-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="af0b4-120">Namespace</span></span>|<span data-ttu-id="af0b4-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="af0b4-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af0b4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af0b4-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
