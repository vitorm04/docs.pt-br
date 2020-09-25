---
title: Processamento de transações
description: Examine o processamento de transações no .NET. As transações garantem que os recursos orientados a dados não sejam atualizados permanentemente a menos que todas as operações sejam concluídas com êxito.
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: bbf2448128da7df8af415ff5dea7e3cd8af24d1e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186803"
---
# <a name="transaction-processing"></a><span data-ttu-id="1ca6a-104">Processamento de transações</span><span class="sxs-lookup"><span data-stu-id="1ca6a-104">Transaction Processing</span></span>

<span data-ttu-id="1ca6a-105">Ao comprar um livro de livrarias online, você troca money (na forma de crédito) de um livro.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-105">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="1ca6a-106">Se o crédito é boa, uma série de operações relacionadas garante que você obtenha o livro e a livraria obtém seu dinheiro.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-106">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="1ca6a-107">No entanto, se uma única operação na série falhar durante a troca, toda a troca falhará.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-107">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="1ca6a-108">Você não obtiver o livro e a livraria não obter seu dinheiro.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-108">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="1ca6a-109">A tecnologia responsável por fazer o intercâmbio equilibrado e previsível é chamada de processamento de transações.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-109">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="1ca6a-110">As transações garantem que recursos orientados a dados não são permanentemente atualizados, a menos que todas as operações dentro da unidade transacional foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-110">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="1ca6a-111">Ao combinar um conjunto de operações relacionadas em uma unidade que completamente obtenha êxito ou falha completamente, você pode simplificar a recuperação de erro e tornar seu aplicativo mais confiável.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-111">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="1ca6a-112">Sistemas de processamento de transação consistem em hardware e software que hospeda um aplicativo orientado a transações que executa as transações de rotina necessárias para conduzir os negócios.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-112">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="1ca6a-113">Os exemplos incluem sistemas de gerenciamento de entrada de ordem de venda, reservas de viagens, folha de pagamento, registros de funcionários, produção e a remessa.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-113">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="1ca6a-114">Esta seção fornece informações gerais sobre o processamento de transações e informações específicas sobre como escrever aplicativos transacionais e gerenciadores de recursos usando o Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-114">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ca6a-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1ca6a-115">In This Section</span></span>  

 [<span data-ttu-id="1ca6a-116">Conceitos básicos de transação</span><span class="sxs-lookup"><span data-stu-id="1ca6a-116">Transaction Fundamentals</span></span>](transaction-fundamentals.md)  
 <span data-ttu-id="1ca6a-117">Apresenta os termos e conceitos de processamento de transações básicas.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-117">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="1ca6a-118">Recursos fornecidos por System.Transactions</span><span class="sxs-lookup"><span data-stu-id="1ca6a-118">Features Provided by System.Transactions</span></span>](features-provided-by-system-transactions.md)  
 <span data-ttu-id="1ca6a-119">Descreve como usar recursos do System. Transactions para escrever seu próprio aplicativo transacional.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-119">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1ca6a-120">Referência</span><span class="sxs-lookup"><span data-stu-id="1ca6a-120">Reference</span></span>  

 <xref:System.Transactions>  
 <span data-ttu-id="1ca6a-121">Fornece classes que permitem que o seu código para participar de transações.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-121">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="1ca6a-122">As classes de suportam a transações com vários participantes distribuídos, várias notificações de fase e inscrições duráveis.</span><span class="sxs-lookup"><span data-stu-id="1ca6a-122">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
