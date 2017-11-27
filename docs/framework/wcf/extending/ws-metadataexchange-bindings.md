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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23752cb259accb1df6093a4b1d90a2541fd771d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="0025c-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="0025c-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="0025c-103">Este tópico descreve como as associações de troca de metadados padrão são construídas para vários transportes.</span><span class="sxs-lookup"><span data-stu-id="0025c-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="0025c-104">As associações padrão</span><span class="sxs-lookup"><span data-stu-id="0025c-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="0025c-105">Nome de associação padrão</span><span class="sxs-lookup"><span data-stu-id="0025c-105">Default Binding Name</span></span>|<span data-ttu-id="0025c-106">Como a associação é construída</span><span class="sxs-lookup"><span data-stu-id="0025c-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="0025c-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0025c-107">MexHttpBinding</span></span>|<span data-ttu-id="0025c-108">Um <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte desabilitada.</span><span class="sxs-lookup"><span data-stu-id="0025c-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="0025c-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="0025c-109">MexHttpsBinding</span></span>|<span data-ttu-id="0025c-110">Um <xref:System.ServiceModel.WSHttpBinding> que dá suporte à segurança de nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="0025c-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="0025c-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="0025c-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="0025c-112">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> usando os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0025c-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="0025c-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="0025c-113">MexTcpBinding</span></span>|<span data-ttu-id="0025c-114">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.TcpTransportBindingElement> usando valores padrão.</span><span class="sxs-lookup"><span data-stu-id="0025c-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
