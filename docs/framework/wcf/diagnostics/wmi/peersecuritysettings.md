---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484512"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="9b41f-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9b41f-102">PeerSecuritySettings</span></span>
<span data-ttu-id="9b41f-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9b41f-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b41f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b41f-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9b41f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9b41f-105">Methods</span></span>  
 <span data-ttu-id="9b41f-106">A classe PeerSecuritySettings não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="9b41f-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9b41f-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9b41f-107">Properties</span></span>  
 <span data-ttu-id="9b41f-108">A classe PeerSecuritySettings tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9b41f-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="9b41f-109">Modo</span><span class="sxs-lookup"><span data-stu-id="9b41f-109">Mode</span></span>  
 <span data-ttu-id="9b41f-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9b41f-110">Data type: string</span></span>  
  
 <span data-ttu-id="9b41f-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="9b41f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b41f-112">Se nível de mensagem e segurança em nível de transporte são usados por um ponto de extremidade configurado com a associação.</span><span class="sxs-lookup"><span data-stu-id="9b41f-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="9b41f-113">Transporte</span><span class="sxs-lookup"><span data-stu-id="9b41f-113">Transport</span></span>  
 <span data-ttu-id="9b41f-114">Tipo de dados: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9b41f-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="9b41f-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="9b41f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9b41f-116">Configurações de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="9b41f-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b41f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b41f-117">Requirements</span></span>  
  
|<span data-ttu-id="9b41f-118">MOF</span><span class="sxs-lookup"><span data-stu-id="9b41f-118">MOF</span></span>|<span data-ttu-id="9b41f-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9b41f-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9b41f-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="9b41f-120">Namespace</span></span>|<span data-ttu-id="9b41f-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9b41f-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b41f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b41f-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
