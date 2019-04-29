---
title: WCF e WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768726"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="e4944-102">WCF e WebSockets</span><span class="sxs-lookup"><span data-stu-id="e4944-102">WCF and WebSockets</span></span>
<span data-ttu-id="e4944-103">O .NET Framework 4.5 introduz suporte para WebSockets no Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="e4944-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="e4944-104">WebSockets é uma tecnologia eficiente e com base em padrões que permite a comunicação bidirecional sobre as portas HTTP padrão 80 e 443.</span><span class="sxs-lookup"><span data-stu-id="e4944-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="e4944-105">O uso de portas HTTP padrão permite que o WebSockets comunique-se por meio da Web por meio de intermediários.</span><span class="sxs-lookup"><span data-stu-id="e4944-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="e4944-106">Duas novas associações padrão foram adicionadas à comunicação de suporte em um transporte de WebSocket.</span><span class="sxs-lookup"><span data-stu-id="e4944-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="e4944-107"><xref:System.ServiceModel.NetHttpBinding> e <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="e4944-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="e4944-108">Configurações específicas do WebSockets podem ser configuradas na <xref:System.ServiceModel.Channels.HttpTransportBindingElement> acessando o <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4944-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="e4944-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e4944-109">In This Section</span></span>  
 [<span data-ttu-id="e4944-110">Usando o NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e4944-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="e4944-111">Discute o <xref:System.ServiceModel.NetHttpBinding> e como configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="e4944-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="e4944-112">Como: Criar um serviço WCF que se comunica sobre WebSockets</span><span class="sxs-lookup"><span data-stu-id="e4944-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="e4944-113">Descreve como criar um serviço WCF que se comunica sobre Websockets.</span><span class="sxs-lookup"><span data-stu-id="e4944-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e4944-114">Referência</span><span class="sxs-lookup"><span data-stu-id="e4944-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e4944-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e4944-115">Related Sections</span></span>
