---
title: Integração de System.Transactions com o SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 25b443d8234909a4d8525c2ce2b4e70c3baa337b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965229"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="1ca62-102">Integração de System.Transactions com o SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ca62-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="1ca62-103">O .NET Framework versão 2,0 introduziu uma estrutura de transação que pode ser acessada por meio do <xref:System.Transactions> namespace.</span><span class="sxs-lookup"><span data-stu-id="1ca62-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="1ca62-104">Essa estrutura expõe transações de uma maneira totalmente integrada no .NET Framework, incluindo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1ca62-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="1ca62-105">Além dos aprimoramentos de programação, <xref:System.Transactions> e o ADO.net pode trabalhar em conjunto para coordenar otimizações quando você trabalha com transações.</span><span class="sxs-lookup"><span data-stu-id="1ca62-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="1ca62-106">Uma transação promocionaltable é uma transação leve (local) que pode ser promovida automaticamente para uma transação totalmente distribuída conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="1ca62-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="1ca62-107">A partir do ADO.NET 2,0 <xref:System.Data.SqlClient> , o oferece suporte a transações de promoção quando você trabalha com SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1ca62-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="1ca62-108">Uma transação passível de promoção não chama a sobrecarga adicional de uma transação distribuída a menos que a sobrecarga adicional seja necessária.</span><span class="sxs-lookup"><span data-stu-id="1ca62-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="1ca62-109">As transações de promoçãotable são automáticas e não exigem nenhuma intervenção do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="1ca62-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="1ca62-110">As transações de promoçãotable só estão disponíveis quando você usa o .NET Framework provedor de dados para`SqlClient`SQL Server () com SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1ca62-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="1ca62-111">Criando transações de promotable</span><span class="sxs-lookup"><span data-stu-id="1ca62-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="1ca62-112">O provedor de .NET Framework para SQL Server fornece suporte para transações de promoção, que são manipuladas por meio das classes <xref:System.Transactions> no namespace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ca62-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="1ca62-113">As transações da promotable otimizam as transações distribuídas por meio da criação de uma transação distribuída até que seja necessária.</span><span class="sxs-lookup"><span data-stu-id="1ca62-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="1ca62-114">Se apenas um Gerenciador de recursos for necessário, nenhuma transação distribuída ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="1ca62-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ca62-115">Em um cenário parcialmente confiável, o <xref:System.Transactions.DistributedTransactionPermission> é necessário quando uma transação é promovida para uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="1ca62-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="1ca62-116">Cenários de transação de promoção</span><span class="sxs-lookup"><span data-stu-id="1ca62-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="1ca62-117">As transações distribuídas normalmente consomem recursos significativos do sistema, sendo gerenciados pelo Microsoft Coordenador de Transações Distribuídas (MS DTC), que integra todos os gerenciadores de recursos acessados na transação.</span><span class="sxs-lookup"><span data-stu-id="1ca62-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="1ca62-118">Uma transação promocionaltable é uma forma especial de uma <xref:System.Transactions> transação que delega efetivamente o trabalho a uma transação SQL Server simples.</span><span class="sxs-lookup"><span data-stu-id="1ca62-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="1ca62-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>e SQL Server coordenar o trabalho envolvido na manipulação da transação, promovê-la para uma transação distribuída completa, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="1ca62-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="1ca62-120">O benefício de usar transações de promoção é que, quando uma conexão é aberta usando uma transação <xref:System.Transactions.TransactionScope> ativa, e não há nenhuma outra conexão aberta, a transação é confirmada como uma transação leve, em vez de incorrer o adicional sobrecarga de uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="1ca62-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="1ca62-121">Palavras-chave da cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="1ca62-121">Connection String Keywords</span></span>  
 <span data-ttu-id="1ca62-122">A <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Propriedade dá suporte a uma `Enlist`palavra-chave, <xref:System.Data.SqlClient> , que indica se o detectará contextos transacionais e inscreverá automaticamente a conexão em uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="1ca62-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="1ca62-123">Se `Enlist=true`, a conexão será inscrito automaticamente no contexto de transação atual do thread de abertura.</span><span class="sxs-lookup"><span data-stu-id="1ca62-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="1ca62-124">Se `Enlist=false`, a `SqlClient` conexão não interagirá com uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="1ca62-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="1ca62-125">O valor padrão para `Enlist` é true.</span><span class="sxs-lookup"><span data-stu-id="1ca62-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="1ca62-126">Se `Enlist` não for especificado na cadeia de conexão, a conexão será inscrito automaticamente em uma transação distribuída se uma for detectada quando a conexão for aberta.</span><span class="sxs-lookup"><span data-stu-id="1ca62-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="1ca62-127">As `Transaction Binding` palavras-chave em uma <xref:System.Data.SqlClient.SqlConnection> cadeia de conexão controlam a associação da conexão `System.Transactions` com uma transação enlistada.</span><span class="sxs-lookup"><span data-stu-id="1ca62-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="1ca62-128">Ele também está disponível por meio <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> da propriedade de <xref:System.Data.SqlClient.SqlConnectionStringBuilder>a.</span><span class="sxs-lookup"><span data-stu-id="1ca62-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="1ca62-129">A tabela a seguir descreve os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="1ca62-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="1ca62-130">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="1ca62-130">Keyword</span></span>|<span data-ttu-id="1ca62-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="1ca62-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ca62-132">Desassociar implícito</span><span class="sxs-lookup"><span data-stu-id="1ca62-132">Implicit Unbind</span></span>|<span data-ttu-id="1ca62-133">O padrão.</span><span class="sxs-lookup"><span data-stu-id="1ca62-133">The default.</span></span> <span data-ttu-id="1ca62-134">A conexão é desanexada da transação quando termina, voltando para o modo de confirmação automática.</span><span class="sxs-lookup"><span data-stu-id="1ca62-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="1ca62-135">Desassociar explícito</span><span class="sxs-lookup"><span data-stu-id="1ca62-135">Explicit Unbind</span></span>|<span data-ttu-id="1ca62-136">A conexão permanece anexada à transação até que a transação seja fechada.</span><span class="sxs-lookup"><span data-stu-id="1ca62-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="1ca62-137">A conexão falhará se a transação associada não estiver ativa ou não corresponder <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ca62-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="1ca62-138">Usando TransactionScope</span><span class="sxs-lookup"><span data-stu-id="1ca62-138">Using TransactionScope</span></span>  
 <span data-ttu-id="1ca62-139">A <xref:System.Transactions.TransactionScope> classe torna um bloco de código transacional, informando implicitamente as conexões em uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="1ca62-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="1ca62-140">Você deve chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método no final <xref:System.Transactions.TransactionScope> do bloco antes de deixá-lo.</span><span class="sxs-lookup"><span data-stu-id="1ca62-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="1ca62-141">Deixar o bloco invoca o <xref:System.Transactions.TransactionScope.Dispose%2A> método.</span><span class="sxs-lookup"><span data-stu-id="1ca62-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="1ca62-142">Se uma exceção tiver sido gerada que faz com que o código deixe o escopo, a transação será considerada anulada.</span><span class="sxs-lookup"><span data-stu-id="1ca62-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="1ca62-143">É recomendável que você use `using` um bloco para certificar- <xref:System.Transactions.TransactionScope.Dispose%2A> se de que é <xref:System.Transactions.TransactionScope> chamado no objeto quando o bloco Using é encerrado.</span><span class="sxs-lookup"><span data-stu-id="1ca62-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="1ca62-144">A falha na confirmação ou reversão de transações pendentes pode danificar significativamente o desempenho porque o tempo limite <xref:System.Transactions.TransactionScope> padrão para o é de um minuto.</span><span class="sxs-lookup"><span data-stu-id="1ca62-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="1ca62-145">Se `using` você não usar uma instrução, deverá executar todo o trabalho em um `Try` bloco e `Finally` chamar explicitamente o <xref:System.Transactions.TransactionScope.Dispose%2A> método no bloco.</span><span class="sxs-lookup"><span data-stu-id="1ca62-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="1ca62-146">Se ocorrer uma exceção no <xref:System.Transactions.TransactionScope>, a transação será marcada como inconsistente e abandonada.</span><span class="sxs-lookup"><span data-stu-id="1ca62-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="1ca62-147">Ele será revertido quando o <xref:System.Transactions.TransactionScope> for descartado.</span><span class="sxs-lookup"><span data-stu-id="1ca62-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="1ca62-148">Se nenhuma exceção ocorrer, as transações participantes são confirmadas.</span><span class="sxs-lookup"><span data-stu-id="1ca62-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ca62-149">A `TransactionScope` classe cria uma transação com um <xref:System.Transactions.Transaction.IsolationLevel%2A> de `Serializable` por padrão.</span><span class="sxs-lookup"><span data-stu-id="1ca62-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="1ca62-150">Dependendo do seu aplicativo, convém considerar reduzir o nível de isolamento para evitar uma alta contenção em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ca62-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ca62-151">É recomendável que você execute apenas atualizações, inserções e exclusões em transações distribuídas, pois elas consomem recursos de banco de dados significativos.</span><span class="sxs-lookup"><span data-stu-id="1ca62-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="1ca62-152">As instruções SELECT podem bloquear os recursos do banco de dados desnecessariamente e, em alguns cenários, talvez seja necessário usar transações para seleções.</span><span class="sxs-lookup"><span data-stu-id="1ca62-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="1ca62-153">Qualquer trabalho que não seja de banco de dados deve ser feito fora do escopo da transação, a menos que envolva outros gerenciadores de recursos transacionados.</span><span class="sxs-lookup"><span data-stu-id="1ca62-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="1ca62-154">Embora uma exceção no escopo da transação impeça que a transação seja confirmada, a <xref:System.Transactions.TransactionScope> classe não tem provisão para reverter as alterações que seu código fez fora do escopo da própria transação.</span><span class="sxs-lookup"><span data-stu-id="1ca62-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="1ca62-155">Se você precisar executar alguma ação quando a transação for revertida, deverá escrever sua própria implementação da <xref:System.Transactions.IEnlistmentNotification> interface e inscrever-se explicitamente na transação.</span><span class="sxs-lookup"><span data-stu-id="1ca62-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ca62-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1ca62-156">Example</span></span>  
 <span data-ttu-id="1ca62-157">Trabalhar com <xref:System.Transactions> o requer que você tenha uma referência a System. Transactions. dll.</span><span class="sxs-lookup"><span data-stu-id="1ca62-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="1ca62-158">A função a seguir demonstra como criar uma transação promocionaltable em duas instâncias de SQL Server diferentes, representadas por <xref:System.Data.SqlClient.SqlConnection> dois objetos diferentes, que são encapsuladas em um <xref:System.Transactions.TransactionScope> bloco.</span><span class="sxs-lookup"><span data-stu-id="1ca62-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="1ca62-159">O código cria o <xref:System.Transactions.TransactionScope> bloco com uma `using` instrução e abre a primeira conexão, que a <xref:System.Transactions.TransactionScope>lista automaticamente no.</span><span class="sxs-lookup"><span data-stu-id="1ca62-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="1ca62-160">A transação é inicialmente listada como uma transação leve, não uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="1ca62-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="1ca62-161">A segunda conexão será listada <xref:System.Transactions.TransactionScope> somente se o comando na primeira conexão não lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1ca62-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="1ca62-162">Quando a segunda conexão é aberta, a transação é promovida automaticamente para uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="1ca62-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="1ca62-163">O <xref:System.Transactions.TransactionScope.Complete%2A> método é invocado, que confirma a transação somente se nenhuma exceção tiver sido gerada.</span><span class="sxs-lookup"><span data-stu-id="1ca62-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="1ca62-164">Se uma exceção tiver sido lançada em <xref:System.Transactions.TransactionScope> qualquer ponto do bloco, `Complete` não será chamada, e a transação distribuída será revertida quando o <xref:System.Transactions.TransactionScope> for descartado no final de seu `using` bloco.</span><span class="sxs-lookup"><span data-stu-id="1ca62-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ca62-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ca62-165">See also</span></span>

- [<span data-ttu-id="1ca62-166">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="1ca62-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- <span data-ttu-id="1ca62-167">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ca62-167">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
