---
title: Integração de System. Transactions com o SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 31edbc8f4cbb09f8720b373780f1b0646a985b20
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46001846"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="a3dd5-102">Integração de System. Transactions com o SQL Server</span><span class="sxs-lookup"><span data-stu-id="a3dd5-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="a3dd5-103">O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 2.0 introduziu uma estrutura de transação que pode ser acessada por meio de <xref:System.Transactions> namespace.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-103">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="a3dd5-104">Essa estrutura expõe transações de forma que está totalmente integrada a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], incluindo [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3dd5-104">This framework exposes transactions in a way that is fully integrated in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], including [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="a3dd5-105">Além de aprimoramentos de programabilidade <xref:System.Transactions> e [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] podem trabalhar juntos para coordenar as otimizações, quando você trabalha com transações.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-105">In addition to the programmability enhancements, <xref:System.Transactions> and [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="a3dd5-106">Uma transação passível de promoção é uma transação leve (local) que pode ser elevada automaticamente a uma transação totalmente distribuída em uma base conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="a3dd5-107">Começando com [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> dá suporte a transações passíveis de promoção ao trabalhar com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-107">Starting with [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="a3dd5-108">Uma transação passível de promoção não chama a sobrecarga adicional de uma transação distribuída a menos que a sobrecarga adicional seja necessária.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="a3dd5-109">Transações passíveis de promoção são automáticas e não exigem intervenção do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="a3dd5-110">Transações passíveis de promoção só estão disponíveis quando você usa o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider para SQL Server (`SqlClient`) com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-110">Promotable transactions are only available when you use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="a3dd5-111">Criando transações passíveis de promoção</span><span class="sxs-lookup"><span data-stu-id="a3dd5-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="a3dd5-112">O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider para SQL Server fornece suporte para transações passíveis de promoção, que são manipuladas pelas classes na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-112">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="a3dd5-113">Transações passíveis de promoção otimizam transações distribuídas, adiando a criação de uma transação distribuída até que ele seja necessário.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="a3dd5-114">Se houver apenas um Gerenciador de recursos necessário, nenhuma transação distribuída ocorre.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dd5-115">Em um cenário parcialmente confiável, o <xref:System.Transactions.DistributedTransactionPermission> é necessário quando uma transação é promovida a uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="a3dd5-116">Cenários de transação passível de promoção</span><span class="sxs-lookup"><span data-stu-id="a3dd5-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="a3dd5-117">Transações distribuídas normalmente consomem recursos significativos do sistema, que está sendo gerenciados pelo Microsoft Distributed Transaction Coordinator (MS DTC), que integra todos os gerenciadores de recursos acessados na transação.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="a3dd5-118">Uma transação passível de promoção é uma forma especial de um <xref:System.Transactions> transação que delega efetivamente o trabalho para uma simple transação do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="a3dd5-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, e o SQL Server coordenam o trabalho envolvido no tratamento da transação, elevando-a para uma transação distribuída completa conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="a3dd5-120">A vantagem de usar transações passíveis de promoção é que quando uma conexão é aberta por meio de um ativo <xref:System.Transactions.TransactionScope> transação e nenhuma outra conexão aberta, a transação é confirmada como uma transação superficial, em vez de incorrer adicional sobrecarga de uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="a3dd5-121">Palavras-chave de cadeia de caracteres de Conexão</span><span class="sxs-lookup"><span data-stu-id="a3dd5-121">Connection String Keywords</span></span>  
 <span data-ttu-id="a3dd5-122">O <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> propriedade dá suporte a uma palavra-chave `Enlist`, que indica se <xref:System.Data.SqlClient> detecta contextos transacionais e inscrever-se automaticamente a conexão em uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="a3dd5-123">Se `Enlist=true`, a conexão será inscrita automaticamente no contexto de transação atual do thread de abertura.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="a3dd5-124">Se `Enlist=false`, o `SqlClient` conexão não interage com uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="a3dd5-125">O valor padrão para `Enlist` é verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="a3dd5-126">Se `Enlist` não for especificado na cadeia de conexão, a conexão será inscrita automaticamente em uma transação distribuída caso uma seja detectada quando a conexão é aberta.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="a3dd5-127">O `Transaction Binding` palavras-chave em um <xref:System.Data.SqlClient.SqlConnection> cadeia de caracteres de conexão controlar a associação da conexão com um inscrito `System.Transactions` transação.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="a3dd5-128">Ele também está disponível por meio de <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> propriedade de um <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="a3dd5-129">A tabela a seguir descreve os possíveis valores.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="a3dd5-130">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="a3dd5-130">Keyword</span></span>|<span data-ttu-id="a3dd5-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3dd5-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3dd5-132">Implícita desassociar</span><span class="sxs-lookup"><span data-stu-id="a3dd5-132">Implicit Unbind</span></span>|<span data-ttu-id="a3dd5-133">O padrão.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-133">The default.</span></span> <span data-ttu-id="a3dd5-134">A conexão se desconecta da transação quando ele termina, alternando de volta para o modo de confirmação automática.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="a3dd5-135">Explícito desassociar</span><span class="sxs-lookup"><span data-stu-id="a3dd5-135">Explicit Unbind</span></span>|<span data-ttu-id="a3dd5-136">A conexão permanece anexado à transação até que a transação seja fechada.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="a3dd5-137">A conexão falhará se a transação associada não está ativa ou não corresponde ao <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="a3dd5-138">Usando o TransactionScope</span><span class="sxs-lookup"><span data-stu-id="a3dd5-138">Using TransactionScope</span></span>  
 <span data-ttu-id="a3dd5-139">O <xref:System.Transactions.TransactionScope> classe torna um bloco de código transacional inscrevendo implicitamente conexões em uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="a3dd5-140">Você deve chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método no final o <xref:System.Transactions.TransactionScope> bloco antes de deixá-lo.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="a3dd5-141">Sair do bloco invoca o <xref:System.Transactions.TransactionScope.Dispose%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="a3dd5-142">Se uma exceção foi lançada que faz com que o código deixar o escopo, a transação é considerado anulada.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="a3dd5-143">É recomendável que você use uma `using` bloco para certificar-se de que <xref:System.Transactions.TransactionScope.Dispose%2A> é chamado no <xref:System.Transactions.TransactionScope> objeto que o uso do bloco é encerrado.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="a3dd5-144">Falha ao confirmar ou reverter transações pendentes significativamente pode danificar o desempenho porque o tempo limite padrão para o <xref:System.Transactions.TransactionScope> é um minuto.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="a3dd5-145">Se você não usar um `using` instrução, você deve executar todo o trabalho em um `Try` bloquear e chamar explicitamente o <xref:System.Transactions.TransactionScope.Dispose%2A> método no `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="a3dd5-146">Se ocorrer uma exceção no <xref:System.Transactions.TransactionScope>, a transação será marcada como inconsistente e abandonada.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="a3dd5-147">Ela será revertida quando o <xref:System.Transactions.TransactionScope> é descartado.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="a3dd5-148">Se nenhuma exceção ocorrer, confirmar as transações participantes serão.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dd5-149">O `TransactionScope` classe cria uma transação com um <xref:System.Transactions.Transaction.IsolationLevel%2A> de `Serializable` por padrão.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="a3dd5-150">Dependendo do seu aplicativo, você talvez queira considerar abaixar o nível de isolamento para evitar uma contenção elevada em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dd5-151">É recomendável que você execute apenas atualizações, inserções e exclusões em transações distribuídas porque eles consomem recursos significativos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="a3dd5-152">Instruções SELECT podem bloquear recursos do banco de dados desnecessariamente e, em alguns cenários, talvez você precise usar transações para seleções.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="a3dd5-153">Qualquer trabalho de banco de dados não deve ser feito fora do escopo da transação, a menos que ele envolve outros gerenciadores de recursos transacionados.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="a3dd5-154">Embora uma exceção no escopo da transação evitar que a transação seja confirmada, o <xref:System.Transactions.TransactionScope> classe não tem provisão para reverter alterações de seu código tenha feito fora do escopo da própria transação.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="a3dd5-155">Se você tiver que executar alguma ação quando a transação for revertida, você deve escrever sua própria implementação do <xref:System.Transactions.IEnlistmentNotification> de interface e inscrevê-la explicitamente na transação.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3dd5-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3dd5-156">Example</span></span>  
 <span data-ttu-id="a3dd5-157">Trabalhando com <xref:System.Transactions> exige que você tenha uma referência a Transactions.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="a3dd5-158">A função a seguir demonstra como criar uma transação passível de promoção em duas instâncias do SQL Server diferentes, representado por dois diferentes <xref:System.Data.SqlClient.SqlConnection> objetos, que são encapsulados em um <xref:System.Transactions.TransactionScope> bloco.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="a3dd5-159">O código cria o <xref:System.Transactions.TransactionScope> bloco com um `using` instrução e abre a primeira conexão, que inscreve automaticamente no <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="a3dd5-160">A transação é inscrita inicialmente como uma transação superficial, não uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="a3dd5-161">A segunda conexão está inscrita no <xref:System.Transactions.TransactionScope> somente se o comando em que a primeira conexão não gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="a3dd5-162">Quando a segunda conexão for aberta, a transação é promovida automaticamente a uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="a3dd5-163">O <xref:System.Transactions.TransactionScope.Complete%2A> método é invocado, que confirma a transação apenas se nenhuma exceção tiver sido lançada.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="a3dd5-164">Se uma exceção tiver sido lançada em qualquer ponto a <xref:System.Transactions.TransactionScope> bloco, `Complete` será não ser chamado e a transação distribuída será revertida quando o <xref:System.Transactions.TransactionScope> é descartada no final do seu `using` bloco.</span><span class="sxs-lookup"><span data-stu-id="a3dd5-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3dd5-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3dd5-165">See Also</span></span>  
 [<span data-ttu-id="a3dd5-166">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="a3dd5-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="a3dd5-167">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a3dd5-167">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
