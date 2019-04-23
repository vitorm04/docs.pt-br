---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980428"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="b352b-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b352b-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="b352b-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b352b-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b352b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b352b-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b352b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b352b-105">Methods</span></span>  
 <span data-ttu-id="b352b-106">A classe PeerTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="b352b-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b352b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b352b-107">Properties</span></span>  
 <span data-ttu-id="b352b-108">A classe PeerTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b352b-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="b352b-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="b352b-109">ListenIPAddress</span></span>  
 <span data-ttu-id="b352b-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b352b-110">Data type: string</span></span>  
  
 <span data-ttu-id="b352b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="b352b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b352b-112">O endereço IP no qual o nó par escuta para mensagens.</span><span class="sxs-lookup"><span data-stu-id="b352b-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="b352b-113">Porta</span><span class="sxs-lookup"><span data-stu-id="b352b-113">Port</span></span>  
 <span data-ttu-id="b352b-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="b352b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b352b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="b352b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b352b-116">A porta de interface de rede na qual o mensagens do canal de pares de processos de associação.</span><span class="sxs-lookup"><span data-stu-id="b352b-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="b352b-117">Segurança</span><span class="sxs-lookup"><span data-stu-id="b352b-117">Security</span></span>  
 <span data-ttu-id="b352b-118">Tipo de dados: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="b352b-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="b352b-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="b352b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b352b-120">Configurações de segurança de transporte de par.</span><span class="sxs-lookup"><span data-stu-id="b352b-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b352b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b352b-121">Requirements</span></span>  
  
|<span data-ttu-id="b352b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b352b-122">MOF</span></span>|<span data-ttu-id="b352b-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b352b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b352b-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="b352b-124">Namespace</span></span>|<span data-ttu-id="b352b-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b352b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b352b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b352b-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
