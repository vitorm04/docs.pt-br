---
title: Estendendo a camada do canal
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a1a1bb0b1f2c5e6b42ee793f18f5ad442b1fe8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="90f76-102">Estendendo a camada do canal</span><span class="sxs-lookup"><span data-stu-id="90f76-102">Extending the Channel Layer</span></span>
<span data-ttu-id="90f76-103">A camada do canal é responsável para a troca de mensagens entre clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="90f76-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="90f76-104">Extensões de canal podem implementar a nova funcionalidade de protocolo, como segurança ou funcionalidade de transporte, como implementar um novo transporte de rede para transportar mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="90f76-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90f76-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="90f76-105">In This Section</span></span>  
 [<span data-ttu-id="90f76-106">Visão geral do modelo de canal</span><span class="sxs-lookup"><span data-stu-id="90f76-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="90f76-107">Fornece uma visão geral de quais canais serão, os recursos que eles fornecem e como elas funcionam em um serviço e um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="90f76-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="90f76-108">Desenvolvimento de canais</span><span class="sxs-lookup"><span data-stu-id="90f76-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="90f76-109">Descreve detalhadamente as funções que têm vários tipos de infraestrutura de canal, como funciona o ciclo de vida de mecanismo e o estado de estado, a manipulação de exceções e falhas, como implementar o suporte a metadados e como canais funcionam com codificadores de mensagem.</span><span class="sxs-lookup"><span data-stu-id="90f76-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="90f76-110">Codificadores personalizados</span><span class="sxs-lookup"><span data-stu-id="90f76-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="90f76-111">Descreve a função codificadores de mensagem em canais e como criar um.</span><span class="sxs-lookup"><span data-stu-id="90f76-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="90f76-112">Upgrades de fluxo personalizados</span><span class="sxs-lookup"><span data-stu-id="90f76-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="90f76-113">Descreve o processo de atualização os fluxos fornecidos por transportes voltados para o fluxo.</span><span class="sxs-lookup"><span data-stu-id="90f76-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>
