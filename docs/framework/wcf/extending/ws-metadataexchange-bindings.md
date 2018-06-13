---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488618"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="53b0e-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="53b0e-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="53b0e-103">Este tópico descreve como as associações de troca de metadados padrão são construídas para vários transportes.</span><span class="sxs-lookup"><span data-stu-id="53b0e-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="53b0e-104">As associações padrão</span><span class="sxs-lookup"><span data-stu-id="53b0e-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="53b0e-105">Nome de associação padrão</span><span class="sxs-lookup"><span data-stu-id="53b0e-105">Default Binding Name</span></span>|<span data-ttu-id="53b0e-106">Como a associação é construída</span><span class="sxs-lookup"><span data-stu-id="53b0e-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="53b0e-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="53b0e-107">MexHttpBinding</span></span>|<span data-ttu-id="53b0e-108">Um <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte desabilitada.</span><span class="sxs-lookup"><span data-stu-id="53b0e-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="53b0e-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="53b0e-109">MexHttpsBinding</span></span>|<span data-ttu-id="53b0e-110">Um <xref:System.ServiceModel.WSHttpBinding> que dá suporte à segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="53b0e-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="53b0e-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="53b0e-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="53b0e-112">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> usando os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="53b0e-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="53b0e-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="53b0e-113">MexTcpBinding</span></span>|<span data-ttu-id="53b0e-114">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.TcpTransportBindingElement> usando valores padrão.</span><span class="sxs-lookup"><span data-stu-id="53b0e-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
