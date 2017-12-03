---
title: WS-MetadataExchange Bindings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="108e7-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="108e7-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="108e7-103">Este tópico descreve como as associações de troca de metadados padrão são construídas para vários transportes.</span><span class="sxs-lookup"><span data-stu-id="108e7-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="108e7-104">As associações padrão</span><span class="sxs-lookup"><span data-stu-id="108e7-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="108e7-105">Nome de associação padrão</span><span class="sxs-lookup"><span data-stu-id="108e7-105">Default Binding Name</span></span>|<span data-ttu-id="108e7-106">Como a associação é construída</span><span class="sxs-lookup"><span data-stu-id="108e7-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="108e7-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="108e7-107">MexHttpBinding</span></span>|<span data-ttu-id="108e7-108">Um <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte desabilitada.</span><span class="sxs-lookup"><span data-stu-id="108e7-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="108e7-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="108e7-109">MexHttpsBinding</span></span>|<span data-ttu-id="108e7-110">Um <xref:System.ServiceModel.WSHttpBinding> que dá suporte à segurança de nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="108e7-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="108e7-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="108e7-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="108e7-112">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> usando os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="108e7-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="108e7-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="108e7-113">MexTcpBinding</span></span>|<span data-ttu-id="108e7-114">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.TcpTransportBindingElement> usando valores padrão.</span><span class="sxs-lookup"><span data-stu-id="108e7-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
