---
title: Modelos de transação
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050773"
---
# <a name="transaction-models"></a><span data-ttu-id="b7d8e-102">Modelos de transação</span><span class="sxs-lookup"><span data-stu-id="b7d8e-102">Transaction Models</span></span>
<span data-ttu-id="b7d8e-103">Este tópico descreve a relação entre os modelos de programação de transação e a Microsoft fornece os componentes da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="b7d8e-104">Ao usar transações no Windows Communication Foundation (WCF), é importante entender que você estiver não selecionando entre diferentes modelos transacionais, mas em vez disso, operando em diferentes camadas de um modelo consistente e integrado.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="b7d8e-105">As seções a seguir descrevem os três componentes de transação principal.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="b7d8e-106">Transações do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="b7d8e-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="b7d8e-107">O suporte a transações no WCF permite que você escrever serviços transacionais.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="b7d8e-108">Além disso, com seu suporte para o protocolo WS-AtomicTransaction (WS-AT), aplicativos podem fluir transações a serviços Web criados usando o WCF ou tecnologia de produtos de terceiros.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="b7d8e-109">Em um aplicativo ou serviço do WCF, recursos de transação do WCF fornecem atributos e a configuração para especificar declarativamente como e quando a infraestrutura deve criar, fluxo e sincronizar as transações.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="b7d8e-110">Transações de System. Transactions</span><span class="sxs-lookup"><span data-stu-id="b7d8e-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="b7d8e-111">O <xref:System.Transactions> namespace fornece dois um modelo de programação explícito com base em de <xref:System.Transactions.Transaction> classe, bem como um modelo de programação implícito usando a <xref:System.Transactions.TransactionScope> classe, em que a infra-estrutura gerencia automaticamente as transações.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="b7d8e-112">Para obter mais informações sobre como criar um aplicativo transacional usando esses dois modelos, consulte [escrevendo um aplicativo transacional](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="b7d8e-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="b7d8e-113">Em um aplicativo, ou um serviço WCF <xref:System.Transactions> fornece o modelo de programação para criação de transações em um aplicativo cliente e explicitamente interagindo com uma transação, quando necessário, dentro de um serviço.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="b7d8e-114">Transações do MSDTC</span><span class="sxs-lookup"><span data-stu-id="b7d8e-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="b7d8e-115">O Microsoft Distributed Transaction Coordinator (MSDTC) é um Gerenciador de transações que fornece suporte para transações distribuídas.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="b7d8e-116">Para obter mais informações, consulte o [referência do programador de DTC](https://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="b7d8e-116">For more information, see the [DTC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="b7d8e-117">Em um aplicativo ou serviço do WCF, o MSDTC fornece a infraestrutura para a coordenação de transações criadas dentro de um cliente ou serviço.</span><span class="sxs-lookup"><span data-stu-id="b7d8e-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
