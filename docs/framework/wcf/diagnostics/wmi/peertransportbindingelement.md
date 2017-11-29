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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="11cd9-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="11cd9-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="11cd9-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="11cd9-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11cd9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11cd9-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="11cd9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="11cd9-105">Methods</span></span>  
 <span data-ttu-id="11cd9-106">A classe PeerTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="11cd9-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="11cd9-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="11cd9-107">Properties</span></span>  
 <span data-ttu-id="11cd9-108">A classe PeerTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="11cd9-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="11cd9-109">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="11cd9-109">ListenIPAddress</span></span>  
 <span data-ttu-id="11cd9-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="11cd9-110">Data type: string</span></span>  
  
 <span data-ttu-id="11cd9-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="11cd9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11cd9-112">O endereço IP no qual o nó par escuta as mensagens.</span><span class="sxs-lookup"><span data-stu-id="11cd9-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="11cd9-113">Porta</span><span class="sxs-lookup"><span data-stu-id="11cd9-113">Port</span></span>  
 <span data-ttu-id="11cd9-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="11cd9-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="11cd9-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="11cd9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11cd9-116">A porta de interface de rede no qual essa processos de associação pares de mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="11cd9-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="11cd9-117">Segurança</span><span class="sxs-lookup"><span data-stu-id="11cd9-117">Security</span></span>  
 <span data-ttu-id="11cd9-118">Tipo de dados: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="11cd9-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="11cd9-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="11cd9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11cd9-120">Configurações de segurança de transporte ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="11cd9-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11cd9-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11cd9-121">Requirements</span></span>  
  
|<span data-ttu-id="11cd9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="11cd9-122">MOF</span></span>|<span data-ttu-id="11cd9-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="11cd9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="11cd9-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="11cd9-124">Namespace</span></span>|<span data-ttu-id="11cd9-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="11cd9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11cd9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11cd9-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
