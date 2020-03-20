---
title: Integração de System.Transactions com o SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174232"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="ed89c-102">Integração de System.Transactions com o SQL Server</span><span class="sxs-lookup"><span data-stu-id="ed89c-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="ed89c-103">A versão 2.0 do .NET Framework introduziu uma <xref:System.Transactions> estrutura de transação que pode ser acessada através do namespace.</span><span class="sxs-lookup"><span data-stu-id="ed89c-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="ed89c-104">Essa estrutura expõe as transações de forma totalmente integrada ao Quadro .NET, incluindo ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ed89c-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="ed89c-105">Além dos aprimoramentos de <xref:System.Transactions> programação, e ADO.NET podem trabalhar em conjunto para coordenar otimizações quando você trabalha com transações.</span><span class="sxs-lookup"><span data-stu-id="ed89c-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="ed89c-106">Uma transação promovidada é uma transação leve (local) que pode ser automaticamente promovida para uma transação totalmente distribuída conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="ed89c-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="ed89c-107">Começando com ADO.NET 2.0, <xref:System.Data.SqlClient> suporta transações promotáveis quando você trabalha com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ed89c-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="ed89c-108">Uma transação passível de promoção não chama a sobrecarga adicional de uma transação distribuída a menos que a sobrecarga adicional seja necessária.</span><span class="sxs-lookup"><span data-stu-id="ed89c-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="ed89c-109">As transações promovidas são automáticas e não requerem nenhuma intervenção do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="ed89c-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="ed89c-110">As transações promoviais só estão disponíveis quando você usa o`SqlClient`.NET Framework Data Provider for SQL Server ( ) com o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ed89c-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="ed89c-111">Criando transações promotáveis</span><span class="sxs-lookup"><span data-stu-id="ed89c-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="ed89c-112">O .NET Framework Provider for SQL Server fornece suporte para transações promoviadas, <xref:System.Transactions> que são tratadas através das classes no namespace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed89c-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="ed89c-113">As transações promovidas otimizam as transações distribuídas, adiando a criação de uma transação distribuída até que seja necessária.</span><span class="sxs-lookup"><span data-stu-id="ed89c-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="ed89c-114">Se apenas um gerenciador de recursos for necessário, nenhuma transação distribuída ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="ed89c-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed89c-115">Em um cenário parcialmente <xref:System.Transactions.DistributedTransactionPermission> confiável, o é necessário quando uma transação é promovida a uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="ed89c-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="ed89c-116">Cenários de transações promoviais</span><span class="sxs-lookup"><span data-stu-id="ed89c-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="ed89c-117">As transações distribuídas normalmente consomem recursos significativos do sistema, sendo gerenciadas pelo Microsoft Distributed Transaction Coordinator (MS DTC), que integra todos os gerenciadores de recursos acessados na transação.</span><span class="sxs-lookup"><span data-stu-id="ed89c-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="ed89c-118">Uma transação promovidada é <xref:System.Transactions> uma forma especial de uma transação que efetivamente delega o trabalho a uma simples transação sql server.</span><span class="sxs-lookup"><span data-stu-id="ed89c-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="ed89c-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>e o SQL Server coordenam o trabalho envolvido na movimentação da transação, promovendo-a para uma transação distribuída completa, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="ed89c-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="ed89c-120">A vantagem de usar transações promoviais é que <xref:System.Transactions.TransactionScope> quando uma conexão é aberta usando uma transação ativa, e nenhuma outra conexão é aberta, a transação se compromete como uma transação leve, em vez de incorrer na sobrecarga adicional de uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="ed89c-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="ed89c-121">Palavras-chave de cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="ed89c-121">Connection String Keywords</span></span>  
 <span data-ttu-id="ed89c-122">A <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> propriedade suporta uma `Enlist`palavra-chave, <xref:System.Data.SqlClient> que indica se detectará contextos transacionais e alistará automaticamente a conexão em uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="ed89c-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="ed89c-123">Se `Enlist=true`, a conexão é automaticamente alistada no contexto atual de transação do segmento de abertura.</span><span class="sxs-lookup"><span data-stu-id="ed89c-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="ed89c-124">Se `Enlist=false`, `SqlClient` a conexão não interagir com uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="ed89c-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="ed89c-125">O valor `Enlist` padrão para é verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="ed89c-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="ed89c-126">Se `Enlist` não for especificado na seqüência de conexões, a conexão será automaticamente alistada em uma transação distribuída se for detectada quando a conexão for aberta.</span><span class="sxs-lookup"><span data-stu-id="ed89c-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="ed89c-127">As `Transaction Binding` palavras-chave <xref:System.Data.SqlClient.SqlConnection> em uma seqüência de conexões controlam a associação da conexão com uma `System.Transactions` transação alistada.</span><span class="sxs-lookup"><span data-stu-id="ed89c-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="ed89c-128">Também está disponível <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> através <xref:System.Data.SqlClient.SqlConnectionStringBuilder>da propriedade de um .</span><span class="sxs-lookup"><span data-stu-id="ed89c-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="ed89c-129">A tabela a seguir descreve os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="ed89c-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="ed89c-130">Palavra-chave</span><span class="sxs-lookup"><span data-stu-id="ed89c-130">Keyword</span></span>|<span data-ttu-id="ed89c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed89c-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed89c-132">Desvincular implícita</span><span class="sxs-lookup"><span data-stu-id="ed89c-132">Implicit Unbind</span></span>|<span data-ttu-id="ed89c-133">O padrão.</span><span class="sxs-lookup"><span data-stu-id="ed89c-133">The default.</span></span> <span data-ttu-id="ed89c-134">A conexão se desprende da transação quando termina, mudando de volta para o modo de confirmação automática.</span><span class="sxs-lookup"><span data-stu-id="ed89c-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="ed89c-135">Desvincular explícito</span><span class="sxs-lookup"><span data-stu-id="ed89c-135">Explicit Unbind</span></span>|<span data-ttu-id="ed89c-136">A conexão permanece anexada à transação até que a transação seja encerrada.</span><span class="sxs-lookup"><span data-stu-id="ed89c-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="ed89c-137">A conexão falhará se a transação <xref:System.Transactions.Transaction.Current%2A>associada não estiver ativa ou não corresponder .</span><span class="sxs-lookup"><span data-stu-id="ed89c-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="ed89c-138">Usando transactionscope</span><span class="sxs-lookup"><span data-stu-id="ed89c-138">Using TransactionScope</span></span>  
 <span data-ttu-id="ed89c-139">Uma classe <xref:System.Transactions.TransactionScope> torna um bloco de código transacional inscrevendo implicitamente conexões em uma transação distribuída.</span><span class="sxs-lookup"><span data-stu-id="ed89c-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="ed89c-140">Você deve <xref:System.Transactions.TransactionScope.Complete%2A> chamar o método <xref:System.Transactions.TransactionScope> no final do bloco antes de deixá-lo.</span><span class="sxs-lookup"><span data-stu-id="ed89c-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="ed89c-141">Sair do bloco <xref:System.Transactions.TransactionScope.Dispose%2A> invoca o método.</span><span class="sxs-lookup"><span data-stu-id="ed89c-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="ed89c-142">Se uma exceção foi lançada que faz com que o código saia do escopo, a transação é considerada abortada.</span><span class="sxs-lookup"><span data-stu-id="ed89c-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="ed89c-143">Recomendamos que você `using` use um <xref:System.Transactions.TransactionScope.Dispose%2A> bloco para <xref:System.Transactions.TransactionScope> certificar-se de que é chamado no objeto quando o bloco de uso é saído.</span><span class="sxs-lookup"><span data-stu-id="ed89c-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="ed89c-144">A falha em cometer ou reverter transações pendentes pode prejudicar significativamente o desempenho, porque o tempo de intervalo padrão para o <xref:System.Transactions.TransactionScope> é de um minuto.</span><span class="sxs-lookup"><span data-stu-id="ed89c-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="ed89c-145">Se você não usar uma instrução `using`, deverá executar todo o trabalho em um bloco `Try` e chamar explicitamente o método <xref:System.Transactions.TransactionScope.Dispose%2A> no bloco `Finally`.</span><span class="sxs-lookup"><span data-stu-id="ed89c-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="ed89c-146">Se ocorrer uma <xref:System.Transactions.TransactionScope>exceção no , a transação é marcada como inconsistente e é abandonada.</span><span class="sxs-lookup"><span data-stu-id="ed89c-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="ed89c-147">Será revertido quando <xref:System.Transactions.TransactionScope> o descarte for descartado.</span><span class="sxs-lookup"><span data-stu-id="ed89c-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="ed89c-148">Se nenhuma exceção ocorrer, as transações participantes serão confirmadas.</span><span class="sxs-lookup"><span data-stu-id="ed89c-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed89c-149">Por padrão, a classe `TransactionScope` cria uma transação com um <xref:System.Transactions.Transaction.IsolationLevel%2A> de `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="ed89c-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="ed89c-150">Dependendo do seu aplicativo, talvez você queira considerar abaixar o nível de isolamento para evitar uma contenção elevada em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ed89c-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed89c-151">Recomendamos que você execute apenas atualizações, inserções e exclusões em transações distribuídas porque consomem recursos significativos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="ed89c-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="ed89c-152">As instruções selecionadas podem bloquear os recursos do banco de dados desnecessariamente e, em alguns cenários, você pode ter que usar transações para seleções.</span><span class="sxs-lookup"><span data-stu-id="ed89c-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="ed89c-153">Qualquer trabalho não-banco de dados deve ser feito fora do escopo da transação, a menos que envolva outros gestores de recursos transacionados.</span><span class="sxs-lookup"><span data-stu-id="ed89c-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="ed89c-154">Embora uma exceção no escopo da transação impeça <xref:System.Transactions.TransactionScope> a transação de cometer, a classe não tem nenhuma provisão para reverter quaisquer alterações que seu código tenha feito fora do escopo da transação em si.</span><span class="sxs-lookup"><span data-stu-id="ed89c-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="ed89c-155">Se você tiver que tomar alguma ação quando a transação for <xref:System.Transactions.IEnlistmentNotification> revertida, você deve escrever sua própria implementação da interface e se alistar explicitamente na transação.</span><span class="sxs-lookup"><span data-stu-id="ed89c-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed89c-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed89c-156">Example</span></span>  
 <span data-ttu-id="ed89c-157">Trabalhar <xref:System.Transactions> com requer que você tenha uma referência ao System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="ed89c-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="ed89c-158">A função a seguir demonstra como criar uma transação promotora contra <xref:System.Data.SqlClient.SqlConnection> duas instâncias diferentes <xref:System.Transactions.TransactionScope> do SQL Server, representadas por dois objetos diferentes, que estão envoltos em um bloco.</span><span class="sxs-lookup"><span data-stu-id="ed89c-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="ed89c-159">O código <xref:System.Transactions.TransactionScope> cria o `using` bloco com uma declaração e abre a <xref:System.Transactions.TransactionScope>primeira conexão, que o alista automaticamente no .</span><span class="sxs-lookup"><span data-stu-id="ed89c-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="ed89c-160">A transação é inscrita inicialmente como uma transação lightweight, não uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="ed89c-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="ed89c-161">A segunda conexão é <xref:System.Transactions.TransactionScope> alistada no único se o comando na primeira conexão não lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ed89c-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="ed89c-162">Quando a segunda conexão é aberta, a transação é automaticamente promovida para uma transação distribuída completa.</span><span class="sxs-lookup"><span data-stu-id="ed89c-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="ed89c-163">O <xref:System.Transactions.TransactionScope.Complete%2A> método é invocado, que compromete a transação apenas se nenhuma exceção tiver sido lançada.</span><span class="sxs-lookup"><span data-stu-id="ed89c-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="ed89c-164">Se uma exceção tiver sido <xref:System.Transactions.TransactionScope> lançada `Complete` em qualquer ponto do bloco, não será <xref:System.Transactions.TransactionScope> chamada, e a `using` transação distribuída será revirada quando a eliminação for descartada no final de seu bloco.</span><span class="sxs-lookup"><span data-stu-id="ed89c-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed89c-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="ed89c-165">See also</span></span>

- [<span data-ttu-id="ed89c-166">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="ed89c-166">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="ed89c-167">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ed89c-167">ADO.NET Overview</span></span>](ado-net-overview.md)
