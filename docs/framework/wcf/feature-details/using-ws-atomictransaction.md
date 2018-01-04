---
title: "Utilizando Transações WS-Atomic"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 124c5dc0f6db94ae459fe140bd7a4290aa56e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-ws-atomictransaction"></a><span data-ttu-id="21c94-102">Utilizando Transações WS-Atomic</span><span class="sxs-lookup"><span data-stu-id="21c94-102">Using WS-AtomicTransaction</span></span>
<span data-ttu-id="21c94-103">WS-AtomicTransaction (WS-AT) é um protocolo de transação interoperável.</span><span class="sxs-lookup"><span data-stu-id="21c94-103">WS-AtomicTransaction (WS-AT) is an interoperable transaction protocol.</span></span> <span data-ttu-id="21c94-104">Permite o fluxo de transações distribuídas por meio de mensagens do serviço Web e coordenar de maneira interoperável entre infraestruturas de transação heterogêneos.</span><span class="sxs-lookup"><span data-stu-id="21c94-104">It enables you to flow distributed transactions by using Web service messages, and coordinate in an interoperable manner between heterogeneous transaction infrastructures.</span></span> <span data-ttu-id="21c94-105">WS-AT usa o protocolo de confirmação de duas fases para direcionar um resultado atômico entre aplicativos distribuídos, gerenciadores de transações e os gerenciadores de recursos.</span><span class="sxs-lookup"><span data-stu-id="21c94-105">WS-AT uses the two-phase commit protocol to drive an atomic outcome between distributed applications, transaction managers, and resource managers.</span></span>  
  
 <span data-ttu-id="21c94-106">A implementação de WS-AT [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fornece inclui um serviço de protocolo incorporado ao Gerenciador de transações do coordenador de transações distribuídas da Microsoft (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="21c94-106">The WS-AT implementation [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides includes a protocol service built into the Microsoft Distributed Transaction Coordinator (MSDTC) transaction manager.</span></span> <span data-ttu-id="21c94-107">Usando o WS-AT [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos possam fluir transações para outros aplicativos, incluindo os serviços da Web interoperáveis construídos usando a tecnologia de terceiros.</span><span class="sxs-lookup"><span data-stu-id="21c94-107">Using WS-AT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can flow transactions to other applications, including interoperable Web services built using third-party technology.</span></span>  
  
 <span data-ttu-id="21c94-108">Quando uma transação entre um aplicativo cliente e um aplicativo de servidor de fluxo, o protocolo de transação usado é determinado pela associação que o servidor expõe no ponto de extremidade de cliente selecionado.</span><span class="sxs-lookup"><span data-stu-id="21c94-108">When flowing a transaction between a client application and a server application, the transaction protocol used is determined by the binding that the server exposes on the endpoint the client selected.</span></span> <span data-ttu-id="21c94-109">Alguns [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] padrão de associações fornecidas pelo sistema para especificar o `OleTransactions` protocolo como o formato de propagação de transação, enquanto outros padrão à especificação WS-AT.</span><span class="sxs-lookup"><span data-stu-id="21c94-109">Some [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided bindings default to specifying the `OleTransactions` protocol as the transaction propagation format, while others default to specifying WS-AT.</span></span> <span data-ttu-id="21c94-110">Você pode modificar também programaticamente a opção de protocolo de transação dentro de uma associação fornecida.</span><span class="sxs-lookup"><span data-stu-id="21c94-110">You can also programmatically modify the choice of transaction protocol inside a given binding.</span></span>  
  
 <span data-ttu-id="21c94-111">A escolha de protocol influencia:</span><span class="sxs-lookup"><span data-stu-id="21c94-111">The choice of protocol influences:</span></span>  
  
-   <span data-ttu-id="21c94-112">O formato dos cabeçalhos de mensagem usado para a transação do cliente ao servidor de fluxo.</span><span class="sxs-lookup"><span data-stu-id="21c94-112">The format of the message headers used to flow the transaction from client to server.</span></span>  
  
-   <span data-ttu-id="21c94-113">O protocolo de rede usado para executar o protocolo de confirmação de duas fases entre o Gerenciador de transações do cliente e da transação do servidor, para resolver o resultado da transação.</span><span class="sxs-lookup"><span data-stu-id="21c94-113">The network protocol used to run the two-phase commit protocol between the client's transaction manager and the server's transaction, in order to resolve the outcome of the transaction.</span></span>  
  
 <span data-ttu-id="21c94-114">Se o cliente e servidor são escritos usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você não precisa usar WS-AT.</span><span class="sxs-lookup"><span data-stu-id="21c94-114">If the server and client are written using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you do not need to use WS-AT.</span></span> <span data-ttu-id="21c94-115">Em vez disso, você pode usar as configurações padrão de `NetTcpBinding` com o `TransactionFlow` atributo habilitado, que usará o `OleTransactions` protocolo em vez disso.</span><span class="sxs-lookup"><span data-stu-id="21c94-115">Instead, you can use the default settings of `NetTcpBinding` with the `TransactionFlow` attribute enabled, which will use the `OleTransactions` protocol instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="21c94-116">[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="21c94-116"> [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span> <span data-ttu-id="21c94-117">Caso contrário, se o fluxo de transações para serviços da Web criados nas tecnologias de terceiros, você deve usar WS-AT.</span><span class="sxs-lookup"><span data-stu-id="21c94-117">Otherwise, if you are flowing transactions to Web services built on third-party technologies, you must use WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c94-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21c94-118">See Also</span></span>  
 [<span data-ttu-id="21c94-119">Configurando o suporte a transações WS-Atomic</span><span class="sxs-lookup"><span data-stu-id="21c94-119">Configuring WS-Atomic Transaction Support</span></span>](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
