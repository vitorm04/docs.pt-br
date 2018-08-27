---
title: Simultaneidade otimista
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 0b4cdfa7bab1f41f80926b20da3e63a72a2d165d
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42911994"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="cb895-102">Simultaneidade otimista</span><span class="sxs-lookup"><span data-stu-id="cb895-102">Optimistic Concurrency</span></span>
<span data-ttu-id="cb895-103">Em um ambiente multiusuário, há dois modelos para atualizar dados em um banco de dados: simultaneidade otimista e simultaneidade pessimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="cb895-104">O objeto <xref:System.Data.DataSet> é criado para incentivar o uso da simultaneidade otimista para atividades de execução longa, como a comunicação remota de dados e a interação com dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="cb895-105">A simultaneidade pessimista envolve o bloqueio de linhas na fonte de dados para evitar que outros usuários modifiquem dados de uma maneira que afete o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="cb895-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="cb895-106">Em um modelo pessimista, quando um usuário executa uma ação que causa um bloqueio a ser aplicado, outros usuários não podem executar ações que entrem em conflito com o bloqueio até que o proprietário do bloqueio o libere.</span><span class="sxs-lookup"><span data-stu-id="cb895-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="cb895-107">Esse modelo é usado principalmente em ambientes onde há uma grande contenção de dados, de forma que o custo para proteger dados com bloqueios seja menor do que o custo para reverter transações, em caso de conflitos de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cb895-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="cb895-108">Portanto, em um modelo pessimista de simultaneidade, um usuário que atualiza uma linha estabelece um bloqueio.</span><span class="sxs-lookup"><span data-stu-id="cb895-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="cb895-109">Até que o usuário conclua a atualização e libere o bloqueio, ninguém mais pode alterar essa linha.</span><span class="sxs-lookup"><span data-stu-id="cb895-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="cb895-110">Por esse motivo, a simultaneidade pessimista é melhor implementada quando o tempo de bloqueio é curto, como ocorre no processamento programático de registros.</span><span class="sxs-lookup"><span data-stu-id="cb895-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="cb895-111">A simultaneidade pessimista não é uma opção escalonável quando os usuários interagem com dados e levam ao bloqueio de registros por períodos de tempo relativamente longos.</span><span class="sxs-lookup"><span data-stu-id="cb895-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb895-112">Se você precisa atualizar várias linhas na mesma operação, então criar uma transação é uma opção mais escalonável do que usar o bloqueio pessimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="cb895-113">Por outro lado, os usuários que usam a simultaneidade otimista não bloqueiam uma linha ao lê-la.</span><span class="sxs-lookup"><span data-stu-id="cb895-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="cb895-114">Quando um usuário deseja atualizar uma linha, o aplicativo deve determinar se outro usuário alterou a linha após sua leitura.</span><span class="sxs-lookup"><span data-stu-id="cb895-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="cb895-115">A simultaneidade otimista é geralmente usada em ambientes com uma baixa contenção de dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="cb895-116">A simultaneidade otimista melhora o desempenho porque nenhum bloqueio de registros é necessário, e o bloqueio de registros exige recursos adicionais do servidor.</span><span class="sxs-lookup"><span data-stu-id="cb895-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="cb895-117">Além disso, para manter bloqueios de registros, é necessária uma conexão persistente com o servidor de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="cb895-118">Como isso não ocorre em um modelo de simultaneidade otimista, conexões com o servidor estão livres para atender um maior número de clientes em menos tempo.</span><span class="sxs-lookup"><span data-stu-id="cb895-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="cb895-119">Em um modelo de simultaneidade otimista, considera-se que uma violação ocorreu se, depois que um usuário recebe um valor do banco de dados, outro usuário altera o valor antes de o primeiro usuário tentar modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="cb895-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="cb895-120">Veja primeiro a descrição do exemplo a seguir para compreender melhor como o servidor resolve uma violação de simultaneidade.</span><span class="sxs-lookup"><span data-stu-id="cb895-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="cb895-121">As tabelas a seguir apresentam um exemplo de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="cb895-122">Às 13h00, o Usuário1 lê uma linha do banco de dados com os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="cb895-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="cb895-123">**CustID LastName FirstName**</span><span class="sxs-lookup"><span data-stu-id="cb895-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="cb895-124">Bob de Smith 101</span><span class="sxs-lookup"><span data-stu-id="cb895-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="cb895-125">Nome da coluna</span><span class="sxs-lookup"><span data-stu-id="cb895-125">Column name</span></span>|<span data-ttu-id="cb895-126">Valor original</span><span class="sxs-lookup"><span data-stu-id="cb895-126">Original value</span></span>|<span data-ttu-id="cb895-127">Valor atual</span><span class="sxs-lookup"><span data-stu-id="cb895-127">Current value</span></span>|<span data-ttu-id="cb895-128">Valor no banco de dados</span><span class="sxs-lookup"><span data-stu-id="cb895-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="cb895-129">CustID</span><span class="sxs-lookup"><span data-stu-id="cb895-129">CustID</span></span>|<span data-ttu-id="cb895-130">101</span><span class="sxs-lookup"><span data-stu-id="cb895-130">101</span></span>|<span data-ttu-id="cb895-131">101</span><span class="sxs-lookup"><span data-stu-id="cb895-131">101</span></span>|<span data-ttu-id="cb895-132">101</span><span class="sxs-lookup"><span data-stu-id="cb895-132">101</span></span>|  
|<span data-ttu-id="cb895-133">LastName</span><span class="sxs-lookup"><span data-stu-id="cb895-133">LastName</span></span>|<span data-ttu-id="cb895-134">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-134">Smith</span></span>|<span data-ttu-id="cb895-135">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-135">Smith</span></span>|<span data-ttu-id="cb895-136">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-136">Smith</span></span>|  
|<span data-ttu-id="cb895-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="cb895-137">FirstName</span></span>|<span data-ttu-id="cb895-138">Bob</span><span class="sxs-lookup"><span data-stu-id="cb895-138">Bob</span></span>|<span data-ttu-id="cb895-139">Bob</span><span class="sxs-lookup"><span data-stu-id="cb895-139">Bob</span></span>|<span data-ttu-id="cb895-140">Bob</span><span class="sxs-lookup"><span data-stu-id="cb895-140">Bob</span></span>|  
  
 <span data-ttu-id="cb895-141">Às 13h01, o Usuário2 lê a mesma linha.</span><span class="sxs-lookup"><span data-stu-id="cb895-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="cb895-142">Às 13:03. o Usuário2 altera **FirstName** de "Bob" para "Robert" e atualiza o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="cb895-143">Nome da coluna</span><span class="sxs-lookup"><span data-stu-id="cb895-143">Column name</span></span>|<span data-ttu-id="cb895-144">Valor original</span><span class="sxs-lookup"><span data-stu-id="cb895-144">Original value</span></span>|<span data-ttu-id="cb895-145">Valor atual</span><span class="sxs-lookup"><span data-stu-id="cb895-145">Current value</span></span>|<span data-ttu-id="cb895-146">Valor no banco de dados</span><span class="sxs-lookup"><span data-stu-id="cb895-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="cb895-147">CustID</span><span class="sxs-lookup"><span data-stu-id="cb895-147">CustID</span></span>|<span data-ttu-id="cb895-148">101</span><span class="sxs-lookup"><span data-stu-id="cb895-148">101</span></span>|<span data-ttu-id="cb895-149">101</span><span class="sxs-lookup"><span data-stu-id="cb895-149">101</span></span>|<span data-ttu-id="cb895-150">101</span><span class="sxs-lookup"><span data-stu-id="cb895-150">101</span></span>|  
|<span data-ttu-id="cb895-151">LastName</span><span class="sxs-lookup"><span data-stu-id="cb895-151">LastName</span></span>|<span data-ttu-id="cb895-152">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-152">Smith</span></span>|<span data-ttu-id="cb895-153">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-153">Smith</span></span>|<span data-ttu-id="cb895-154">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-154">Smith</span></span>|  
|<span data-ttu-id="cb895-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="cb895-155">FirstName</span></span>|<span data-ttu-id="cb895-156">Bob</span><span class="sxs-lookup"><span data-stu-id="cb895-156">Bob</span></span>|<span data-ttu-id="cb895-157">Robert</span><span class="sxs-lookup"><span data-stu-id="cb895-157">Robert</span></span>|<span data-ttu-id="cb895-158">Bob</span><span class="sxs-lookup"><span data-stu-id="cb895-158">Bob</span></span>|  
  
 <span data-ttu-id="cb895-159">A atualização é bem-sucedida pois os valores no banco de dados no momento da atualização coincidem com os valores originais do Usuário2.</span><span class="sxs-lookup"><span data-stu-id="cb895-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="cb895-160">Às 13h05, o Usuário1 altera o nome de “Bob” para “James” e tenta atualizar a linha.</span><span class="sxs-lookup"><span data-stu-id="cb895-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="cb895-161">Nome da coluna</span><span class="sxs-lookup"><span data-stu-id="cb895-161">Column name</span></span>|<span data-ttu-id="cb895-162">Valor original</span><span class="sxs-lookup"><span data-stu-id="cb895-162">Original value</span></span>|<span data-ttu-id="cb895-163">Valor atual</span><span class="sxs-lookup"><span data-stu-id="cb895-163">Current value</span></span>|<span data-ttu-id="cb895-164">Valor no banco de dados</span><span class="sxs-lookup"><span data-stu-id="cb895-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="cb895-165">CustID</span><span class="sxs-lookup"><span data-stu-id="cb895-165">CustID</span></span>|<span data-ttu-id="cb895-166">101</span><span class="sxs-lookup"><span data-stu-id="cb895-166">101</span></span>|<span data-ttu-id="cb895-167">101</span><span class="sxs-lookup"><span data-stu-id="cb895-167">101</span></span>|<span data-ttu-id="cb895-168">101</span><span class="sxs-lookup"><span data-stu-id="cb895-168">101</span></span>|  
|<span data-ttu-id="cb895-169">LastName</span><span class="sxs-lookup"><span data-stu-id="cb895-169">LastName</span></span>|<span data-ttu-id="cb895-170">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-170">Smith</span></span>|<span data-ttu-id="cb895-171">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-171">Smith</span></span>|<span data-ttu-id="cb895-172">Smith</span><span class="sxs-lookup"><span data-stu-id="cb895-172">Smith</span></span>|  
|<span data-ttu-id="cb895-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="cb895-173">FirstName</span></span>|<span data-ttu-id="cb895-174">Bob</span><span class="sxs-lookup"><span data-stu-id="cb895-174">Bob</span></span>|<span data-ttu-id="cb895-175">James</span><span class="sxs-lookup"><span data-stu-id="cb895-175">James</span></span>|<span data-ttu-id="cb895-176">Robert</span><span class="sxs-lookup"><span data-stu-id="cb895-176">Robert</span></span>|  
  
 <span data-ttu-id="cb895-177">Neste ponto, o Usuário1 encontra uma violação de simultaneidade otimista porque o valor no banco de dados (“Robert”) não coincide mais com o valor original que o Usuário1 esperava (“Bob”).</span><span class="sxs-lookup"><span data-stu-id="cb895-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="cb895-178">A violação de simultaneidade permite que você saiba que a atualização falhou.</span><span class="sxs-lookup"><span data-stu-id="cb895-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="cb895-179">Agora é preciso decidir se as alterações fornecidas pelo Usuário2 devem ser substituídas pelas alterações fornecidas pelo Usuário1, ou se convém cancelar as alterações feitas pelo Usuário1.</span><span class="sxs-lookup"><span data-stu-id="cb895-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="cb895-180">Testando violações de simultaneidade otimista</span><span class="sxs-lookup"><span data-stu-id="cb895-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="cb895-181">Há várias técnicas para testar uma violação de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="cb895-182">Uma delas envolve a inclusão de uma coluna de carimbo de data/hora na tabela.</span><span class="sxs-lookup"><span data-stu-id="cb895-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="cb895-183">Os bancos de dados geralmente fornecem a funcionalidade de carimbo de data/hora que pode ser usada para identificar a data e a hora da última atualização do registro.</span><span class="sxs-lookup"><span data-stu-id="cb895-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="cb895-184">Usando essa técnica, uma coluna de carimbo de data/hora é incluída na definição da tabela.</span><span class="sxs-lookup"><span data-stu-id="cb895-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="cb895-185">Sempre que o registro é atualizado, o carimbo de data/hora é atualizado para refletir a data e hora atuais.</span><span class="sxs-lookup"><span data-stu-id="cb895-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="cb895-186">Em um teste para violações de simultaneidade otimista, a coluna de carimbo de data/hora é retornada com qualquer consulta de conteúdo da tabela.</span><span class="sxs-lookup"><span data-stu-id="cb895-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="cb895-187">Quando há uma tentativa de atualização, o valor de carimbo de data/hora no banco de dados é comparado com o valor original de carimbo de data/hora contido na linha alterada.</span><span class="sxs-lookup"><span data-stu-id="cb895-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="cb895-188">Se eles coincidirem, a atualização será executada e a coluna de carimbo de data/hora será atualizada com a hora atual para refletir a atualização.</span><span class="sxs-lookup"><span data-stu-id="cb895-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="cb895-189">Se eles não coincidirem, significa que ocorreu uma violação de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="cb895-190">Outra técnica para testar uma violação de simultaneidade otimista é verificar se todos os valores originais de coluna em uma linha ainda coincidem com aqueles encontrados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="cb895-191">Por exemplo, considere a seguinte consulta:</span><span class="sxs-lookup"><span data-stu-id="cb895-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="cb895-192">Para testar uma violação de simultaneidade otimista ao atualizar uma linha na **Table1**, você emitiria a seguinte instrução de atualização:</span><span class="sxs-lookup"><span data-stu-id="cb895-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="cb895-193">Contanto que os valores originais correspondam aos valores no banco de dados, a atualização será executada.</span><span class="sxs-lookup"><span data-stu-id="cb895-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="cb895-194">Se um valor foi alterado, a atualização não modificará a linha porque a cláusula WHERE não encontrará uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="cb895-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="cb895-195">Observe que é recomendável sempre retornar um valor de chave primária exclusivo em sua consulta.</span><span class="sxs-lookup"><span data-stu-id="cb895-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="cb895-196">Caso contrário, a instrução UPDATE anterior poderá atualizar mais de uma linha, que talvez não seja sua intenção.</span><span class="sxs-lookup"><span data-stu-id="cb895-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="cb895-197">Se uma coluna na sua fonte de dados permitir nulos, talvez você precise estender a cláusula WHERE para verificar uma referência nula correspondente na tabela local e na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="cb895-198">Por exemplo, a instrução UPDATE a seguir verifica se uma referência nula na linha local ainda corresponde a uma referência nula na fonte de dados, ou se o valor na linha local ainda corresponde ao valor na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="cb895-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="cb895-199">Você também pode optar por aplicar critérios menos restritivos ao usar um modelo de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="cb895-200">Por exemplo, o uso apenas das colunas de chave primária na cláusula WHERE faz com que os dados sejam substituídos, independentemente da atualização ou não das outras colunas desde a última consulta.</span><span class="sxs-lookup"><span data-stu-id="cb895-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="cb895-201">Você também pode aplicar uma cláusula WHERE apenas a colunas específicas, resultando na substituição de dados, a menos que campos específicos tenham sido atualizados desde sua última consulta.</span><span class="sxs-lookup"><span data-stu-id="cb895-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="cb895-202">O evento DataAdapter.RowUpdated</span><span class="sxs-lookup"><span data-stu-id="cb895-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="cb895-203">O **RowUpdated** evento do <xref:System.Data.Common.DataAdapter> objeto pode ser usado em conjunto com as técnicas descritas anteriormente, para fornecer uma notificação ao seu aplicativo de violações de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="cb895-204">**RowUpdated** ocorre após cada tentativa de atualizar um **modificado** de linha de uma **conjunto de dados**.</span><span class="sxs-lookup"><span data-stu-id="cb895-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="cb895-205">Isso o habilita a adicionar código de manipulação especial, incluindo o processamento quando ocorre uma exceção, a adicionar informações de erro personalizadas, a adicionar a lógica de repetição e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="cb895-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="cb895-206">O <xref:System.Data.Common.RowUpdatedEventArgs> objeto retorna um **RecordsAffected** propriedade contendo o número de linhas afetadas por um comando de atualização específica para uma linha modificada em uma tabela.</span><span class="sxs-lookup"><span data-stu-id="cb895-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="cb895-207">Definindo o comando de atualização para testar a simultaneidade otimista, o **RecordsAffected** propriedade, como resultado, retornará um valor de 0 quando ocorreu uma violação de simultaneidade otimista, pois nenhum registro foi atualizado.</span><span class="sxs-lookup"><span data-stu-id="cb895-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="cb895-208">Se esse for o caso, uma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="cb895-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="cb895-209">O **RowUpdated** evento permite que você a tratar esta ocorrência e evitar a exceção, definindo um apropriado **Rowupdatedeventargs** valor, como  **Skipcurrentrow**.</span><span class="sxs-lookup"><span data-stu-id="cb895-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="cb895-210">Para obter mais informações sobre o **RowUpdated** evento, consulte [manipulação de eventos DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="cb895-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="cb895-211">Opcionalmente, você pode definir **DataAdapter. Continueupdateonerror** à **verdadeiro**, antes de chamar **atualização**e responder às informações de erro armazenadas do **RowError** propriedade de uma determinada linha quando o **atualização** é concluída.</span><span class="sxs-lookup"><span data-stu-id="cb895-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="cb895-212">Para obter mais informações, consulte [informações de erro de linha](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="cb895-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="cb895-213">Exemplo de simultaneidade otimista</span><span class="sxs-lookup"><span data-stu-id="cb895-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="cb895-214">A seguir está um exemplo simples que define o **UpdateCommand** de uma **DataAdapter** para testar a simultaneidade otimista e, em seguida, usa o **RowUpdated** eventos para testar violações de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="cb895-215">Quando uma violação de simultaneidade otimista é encontrada, o aplicativo define a **RowError** da linha que a atualização foi emitida para refletir uma violação de simultaneidade otimista.</span><span class="sxs-lookup"><span data-stu-id="cb895-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="cb895-216">Observe que os valores de parâmetro passados para a cláusula WHERE do comando UPDATE são mapeados para o **Original** valores de suas respectivas colunas.</span><span class="sxs-lookup"><span data-stu-id="cb895-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb895-217">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb895-217">See Also</span></span>  
 <span data-ttu-id="cb895-218">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="cb895-218">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="cb895-219">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md) (Atualizando fontes de dados com DataAdapters)</span><span class="sxs-lookup"><span data-stu-id="cb895-219">[Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)</span></span>  
 [<span data-ttu-id="cb895-220">Informações de erro de linha</span><span class="sxs-lookup"><span data-stu-id="cb895-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [<span data-ttu-id="cb895-221">Transações e simultaneidade</span><span class="sxs-lookup"><span data-stu-id="cb895-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="cb895-222">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="cb895-222">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
