---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185177"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="c5ab7-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5ab7-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="c5ab7-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5ab7-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ab7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5ab7-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c5ab7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5ab7-105">Methods</span></span>  
 <span data-ttu-id="c5ab7-106">A classe PeerTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="c5ab7-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c5ab7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c5ab7-107">Properties</span></span>  
 <span data-ttu-id="c5ab7-108">A classe PeerTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c5ab7-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="c5ab7-109">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="c5ab7-109">ListenIPAddress</span></span>  
 <span data-ttu-id="c5ab7-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5ab7-110">Data type: string</span></span>  
  
 <span data-ttu-id="c5ab7-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c5ab7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5ab7-112">O endereço IP no qual o nó par escuta para mensagens.</span><span class="sxs-lookup"><span data-stu-id="c5ab7-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="c5ab7-113">Porta</span><span class="sxs-lookup"><span data-stu-id="c5ab7-113">Port</span></span>  
 <span data-ttu-id="c5ab7-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c5ab7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c5ab7-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c5ab7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5ab7-116">A porta de interface de rede na qual o mensagens do canal de pares de processos de associação.</span><span class="sxs-lookup"><span data-stu-id="c5ab7-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="c5ab7-117">Segurança</span><span class="sxs-lookup"><span data-stu-id="c5ab7-117">Security</span></span>  
 <span data-ttu-id="c5ab7-118">Tipo de dados: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c5ab7-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="c5ab7-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c5ab7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5ab7-120">Configurações de segurança de transporte de par.</span><span class="sxs-lookup"><span data-stu-id="c5ab7-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ab7-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5ab7-121">Requirements</span></span>  
  
|<span data-ttu-id="c5ab7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c5ab7-122">MOF</span></span>|<span data-ttu-id="c5ab7-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c5ab7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c5ab7-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="c5ab7-124">Namespace</span></span>|<span data-ttu-id="c5ab7-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5ab7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5ab7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5ab7-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
