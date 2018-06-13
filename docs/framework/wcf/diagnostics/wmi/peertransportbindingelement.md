---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485639"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="e921d-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e921d-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="e921d-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e921d-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e921d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e921d-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e921d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e921d-105">Methods</span></span>  
 <span data-ttu-id="e921d-106">A classe PeerTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="e921d-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e921d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e921d-107">Properties</span></span>  
 <span data-ttu-id="e921d-108">A classe PeerTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e921d-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="e921d-109">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="e921d-109">ListenIPAddress</span></span>  
 <span data-ttu-id="e921d-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e921d-110">Data type: string</span></span>  
  
 <span data-ttu-id="e921d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e921d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e921d-112">O endereço IP no qual o nó par escuta as mensagens.</span><span class="sxs-lookup"><span data-stu-id="e921d-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="e921d-113">Porta</span><span class="sxs-lookup"><span data-stu-id="e921d-113">Port</span></span>  
 <span data-ttu-id="e921d-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e921d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e921d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e921d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e921d-116">A porta de interface de rede no qual essa processos de associação pares de mensagens do canal.</span><span class="sxs-lookup"><span data-stu-id="e921d-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="e921d-117">Segurança</span><span class="sxs-lookup"><span data-stu-id="e921d-117">Security</span></span>  
 <span data-ttu-id="e921d-118">Tipo de dados: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e921d-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="e921d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e921d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e921d-120">Configurações de segurança de transporte ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="e921d-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e921d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e921d-121">Requirements</span></span>  
  
|<span data-ttu-id="e921d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e921d-122">MOF</span></span>|<span data-ttu-id="e921d-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e921d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e921d-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="e921d-124">Namespace</span></span>|<span data-ttu-id="e921d-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e921d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e921d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e921d-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
