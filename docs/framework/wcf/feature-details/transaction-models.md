---
title: Modelos de transação
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499018"
---
# <a name="transaction-models"></a><span data-ttu-id="8cf36-102">Modelos de transação</span><span class="sxs-lookup"><span data-stu-id="8cf36-102">Transaction Models</span></span>
<span data-ttu-id="8cf36-103">Este tópico descreve a relação entre os modelos de programação de transação e os componentes de infraestrutura, a Microsoft fornece.</span><span class="sxs-lookup"><span data-stu-id="8cf36-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="8cf36-104">Ao usar transações no Windows Communication Foundation (WCF), é importante entender que você está não selecionando entre diferentes modelos transacionais, mas em vez disso, operando em diferentes camadas de um modelo consistente e integrada.</span><span class="sxs-lookup"><span data-stu-id="8cf36-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="8cf36-105">As seções a seguir descrevem os três componentes principais de transação.</span><span class="sxs-lookup"><span data-stu-id="8cf36-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="8cf36-106">Transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8cf36-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="8cf36-107">O suporte de transação do WCF permite que você escrever serviços transacionais.</span><span class="sxs-lookup"><span data-stu-id="8cf36-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="8cf36-108">Além disso, com o suporte para o protocolo WS-AtomicTransaction (WS-AT), aplicativos possam fluir transações de serviços da Web criados usando o WCF ou tecnologia de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8cf36-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="8cf36-109">Em um aplicativo ou serviço WCF, recursos de transação do WCF fornecem atributos e configuração para especificar declarativamente como e quando a infraestrutura deve criar, fluxo e sincronizar as transações.</span><span class="sxs-lookup"><span data-stu-id="8cf36-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="8cf36-110">Transações de System. Transactions</span><span class="sxs-lookup"><span data-stu-id="8cf36-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="8cf36-111">O <xref:System.Transactions> namespace fornece dois um modelo de programação explícito com base no <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, em que a infraestrutura gerencia automaticamente as transações.</span><span class="sxs-lookup"><span data-stu-id="8cf36-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="8cf36-112">Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="8cf36-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="8cf36-113">Em um aplicativo, ou um serviço WCF <xref:System.Transactions> fornece o modelo de programação para criar transações dentro de um aplicativo cliente e explicitamente interagindo com uma transação, quando necessário, dentro de um serviço.</span><span class="sxs-lookup"><span data-stu-id="8cf36-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="8cf36-114">Transações do MSDTC</span><span class="sxs-lookup"><span data-stu-id="8cf36-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="8cf36-115">O Microsoft Distributed Transaction MSDTC (coordenador) é um Gerenciador de transações que fornece suporte para transações distribuídas.</span><span class="sxs-lookup"><span data-stu-id="8cf36-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="8cf36-116">Para obter mais informações, consulte o [referência do programador de DTC](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="8cf36-116">For more information, see the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="8cf36-117">Em um aplicativo ou serviço WCF, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.</span><span class="sxs-lookup"><span data-stu-id="8cf36-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
