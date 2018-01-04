---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="99948-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="99948-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="99948-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="99948-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99948-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99948-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="99948-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="99948-105">Methods</span></span>  
 <span data-ttu-id="99948-106">A classe PeerTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="99948-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="99948-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="99948-107">Properties</span></span>  
 <span data-ttu-id="99948-108">A classe PeerTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="99948-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="99948-109">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="99948-109">ListenIPAddress</span></span>  
 <span data-ttu-id="99948-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="99948-110">Data type: string</span></span>  
  
 <span data-ttu-id="99948-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="99948-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99948-112">O endereço IP no qual o nó par escuta as mensagens.</span><span class="sxs-lookup"><span data-stu-id="99948-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="99948-113">Porta</span><span class="sxs-lookup"><span data-stu-id="99948-113">Port</span></span>  
 <span data-ttu-id="99948-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="99948-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="99948-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="99948-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99948-116">A porta de interface de rede no qual essa processos de associação pares de mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="99948-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="99948-117">Segurança</span><span class="sxs-lookup"><span data-stu-id="99948-117">Security</span></span>  
 <span data-ttu-id="99948-118">Tipo de dados: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="99948-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="99948-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="99948-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99948-120">Configurações de segurança de transporte ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="99948-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99948-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99948-121">Requirements</span></span>  
  
|<span data-ttu-id="99948-122">MOF</span><span class="sxs-lookup"><span data-stu-id="99948-122">MOF</span></span>|<span data-ttu-id="99948-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="99948-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="99948-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="99948-124">Namespace</span></span>|<span data-ttu-id="99948-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99948-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99948-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99948-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
