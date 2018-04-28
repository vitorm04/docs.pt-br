---
title: Visão geral de transações do Windows Communication Foundation
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 76edd7cf30d9da06db6e0c2f4624bf9a6d677eca
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="30df3-102">Visão geral de transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="30df3-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="30df3-103">As transações fornecem uma maneira de agrupar um conjunto de ações ou operações em uma única unidade indivisível de execução.</span><span class="sxs-lookup"><span data-stu-id="30df3-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="30df3-104">Uma transação é uma coleção de operações com as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="30df3-104">A transaction is a collection of operations with the following properties:</span></span>  
  
-   <span data-ttu-id="30df3-105">Atomicidade.</span><span class="sxs-lookup"><span data-stu-id="30df3-105">Atomicity.</span></span> <span data-ttu-id="30df3-106">Isso garante que todas as atualizações concluídas em uma transação específica são confirmadas e duráveis ou são todas anuladas e revertidas ao estado anterior.</span><span class="sxs-lookup"><span data-stu-id="30df3-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="30df3-107">Consistência.</span><span class="sxs-lookup"><span data-stu-id="30df3-107">Consistency.</span></span> <span data-ttu-id="30df3-108">Isso garante que as alterações feitas em uma transação representam uma transformação de um estado consistente para outro.</span><span class="sxs-lookup"><span data-stu-id="30df3-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="30df3-109">Por exemplo, uma transação que transfere dinheiro de uma conta bancária para uma conta de economias não altera a quantidade de dinheiro na conta bancária geral.</span><span class="sxs-lookup"><span data-stu-id="30df3-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
-   <span data-ttu-id="30df3-110">Isolamento.</span><span class="sxs-lookup"><span data-stu-id="30df3-110">Isolation.</span></span> <span data-ttu-id="30df3-111">Isso impede que uma transação observar as alterações não confirmadas que pertencem a outras transações simultâneas.</span><span class="sxs-lookup"><span data-stu-id="30df3-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="30df3-112">O isolamento fornece uma abstração de simultaneidade, garantindo uma transação não pode ter um impacto inesperado da execução de outra transação.</span><span class="sxs-lookup"><span data-stu-id="30df3-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
-   <span data-ttu-id="30df3-113">Durabilidade.</span><span class="sxs-lookup"><span data-stu-id="30df3-113">Durability.</span></span> <span data-ttu-id="30df3-114">Isso significa que, depois de confirmada, as atualizações para recursos gerenciados (como um registro de banco de dados) será persistentes diante de falhas.</span><span class="sxs-lookup"><span data-stu-id="30df3-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="30df3-115"> Fornece um conjunto avançado de recursos que permitem a criação de transações distribuídas em seu aplicativo de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="30df3-115"> provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="30df3-116"> implementa o suporte ao protocolo WS-AtomicTransaction (WS-AT) que permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos transações de fluxo para aplicativos interoperáveis, como serviços da Web interoperáveis construídos usando a tecnologia de terceiros.</span><span class="sxs-lookup"><span data-stu-id="30df3-116"> implements support for the WS-AtomicTransaction (WS-AT) protocol that enables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="30df3-117"> também implementa o suporte para o protocolo de transações OLE, que pode ser usado em cenários em que você não precisa interoperabilidade funcionalidade para habilitar o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="30df3-117"> also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="30df3-118">Você pode usar um arquivo de configuração de aplicativo para configurar as ligações para habilitar ou desabilitar o fluxo de transações, bem como definir o protocolo de transação desejadas em uma associação.</span><span class="sxs-lookup"><span data-stu-id="30df3-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="30df3-119">Além disso, você pode definir tempos limite de transação no nível de serviço usando o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="30df3-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="30df3-120">Para obter mais informações, consulte [ativando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="30df3-120">For more information, see [Enabling Transaction Flow](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="30df3-121">Atributos de transação no <xref:System.ServiceModel> namespace permitem que você faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="30df3-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
-   <span data-ttu-id="30df3-122">Configurar o tempo limite de transação e de filtragem no nível de isolamento usando o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="30df3-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="30df3-123">Habilitar a funcionalidade de transações e configurar o comportamento de conclusão de transações usando o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="30df3-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="30df3-124">Use o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos em um método de contrato para exigir, permitir ou negar o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="30df3-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="30df3-125">Para obter mais informações, consulte [atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="30df3-125">For more information, see [ServiceModel Transaction Attributes](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30df3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30df3-126">See Also</span></span>  
 [<span data-ttu-id="30df3-127">Atributos de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30df3-127">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [<span data-ttu-id="30df3-128">Habilitando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="30df3-128">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
