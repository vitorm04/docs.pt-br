---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795467"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="dc383-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="dc383-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="dc383-103">Este tópico descreve como as associações de troca de metadados padrão são construídas para vários transportes.</span><span class="sxs-lookup"><span data-stu-id="dc383-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="dc383-104">As associações padrão</span><span class="sxs-lookup"><span data-stu-id="dc383-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="dc383-105">Nome da associação padrão</span><span class="sxs-lookup"><span data-stu-id="dc383-105">Default Binding Name</span></span>|<span data-ttu-id="dc383-106">Como a associação é construída</span><span class="sxs-lookup"><span data-stu-id="dc383-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="dc383-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="dc383-107">mexHttpBinding</span></span>|<span data-ttu-id="dc383-108">Um <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte desabilitada.</span><span class="sxs-lookup"><span data-stu-id="dc383-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="dc383-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="dc383-109">mexHttpsBinding</span></span>|<span data-ttu-id="dc383-110">Um <xref:System.ServiceModel.WSHttpBinding> que dá suporte à segurança em nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="dc383-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="dc383-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="dc383-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="dc383-112">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> usando os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="dc383-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="dc383-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="dc383-113">mexTcpBinding</span></span>|<span data-ttu-id="dc383-114">Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.TcpTransportBindingElement> usando valores padrão.</span><span class="sxs-lookup"><span data-stu-id="dc383-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
