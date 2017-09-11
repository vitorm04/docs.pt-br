---
title: "Instrução SyncLock | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
dev_langs:
- VB
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 276d4e801333211ca9bd1851008d7f38933a0ad7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="synclock-statement"></a><span data-ttu-id="2b594-102">Instrução SyncLock</span><span class="sxs-lookup"><span data-stu-id="2b594-102">SyncLock Statement</span></span>
<span data-ttu-id="2b594-103">Obtém um bloqueio exclusivo para um bloco de instruções antes de executar o bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b594-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b594-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="2b594-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2b594-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="2b594-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2b594-106">Required.</span></span> <span data-ttu-id="2b594-107">Expressão que é avaliada como uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="2b594-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="2b594-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2b594-108">Optional.</span></span> <span data-ttu-id="2b594-109">Bloco de instruções a serem executadas quando o bloqueio é adquirido.</span><span class="sxs-lookup"><span data-stu-id="2b594-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="2b594-110">Finaliza uma `SyncLock` bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b594-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b594-111">Remarks</span></span>  
 <span data-ttu-id="2b594-112">O `SyncLock` instrução garante que vários segmentos não executem o bloco de declaração ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2b594-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="2b594-113">`SyncLock`impede cada segmento de entrar no bloco até que nenhum outro segmento está executando.</span><span class="sxs-lookup"><span data-stu-id="2b594-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="2b594-114">O uso mais comum de `SyncLock` é para proteger dados de serem atualizados por mais de um segmento simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="2b594-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="2b594-115">Se as instruções que manipulam os dados devem ir até a conclusão sem interrupção, colocá-los dentro de um `SyncLock` bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="2b594-116">Um bloco de declaração protegido por um bloqueio exclusivo às vezes é chamado um *seção crítica*.</span><span class="sxs-lookup"><span data-stu-id="2b594-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2b594-117">Regras</span><span class="sxs-lookup"><span data-stu-id="2b594-117">Rules</span></span>  
  
-   <span data-ttu-id="2b594-118">A ramificação.</span><span class="sxs-lookup"><span data-stu-id="2b594-118">Branching.</span></span> <span data-ttu-id="2b594-119">Você não pode ramificar em um `SyncLock` bloco de fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="2b594-120">Valor de objeto de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2b594-120">Lock Object Value.</span></span> <span data-ttu-id="2b594-121">O valor de `lockobject` não pode ser `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2b594-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="2b594-122">Você deve criar o objeto de bloqueio antes de você usá-lo em um `SyncLock` instrução.</span><span class="sxs-lookup"><span data-stu-id="2b594-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="2b594-123">Você não pode alterar o valor de `lockobject` durante a execução de um `SyncLock` bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="2b594-124">O mecanismo requer que o objeto de bloqueio permaneça inalterado.</span><span class="sxs-lookup"><span data-stu-id="2b594-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="2b594-125">Não é possível usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador em uma `SyncLock` bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2b594-126">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2b594-126">Behavior</span></span>  
  
-   <span data-ttu-id="2b594-127">Mecanismo.</span><span class="sxs-lookup"><span data-stu-id="2b594-127">Mechanism.</span></span> <span data-ttu-id="2b594-128">Quando um segmento atinge o `SyncLock` instrução, ele avalia o `lockobject` expressão e suspende a execução até que ele obtenha um bloqueio exclusivo no objeto retornado pela expressão.</span><span class="sxs-lookup"><span data-stu-id="2b594-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="2b594-129">Quando outro segmento alcança o `SyncLock` instrução, ele não consegue um bloqueio até que o primeiro segmento execute a `End SyncLock` instrução.</span><span class="sxs-lookup"><span data-stu-id="2b594-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="2b594-130">Dados protegidos.</span><span class="sxs-lookup"><span data-stu-id="2b594-130">Protected Data.</span></span> <span data-ttu-id="2b594-131">Se `lockobject` é um `Shared` variável, o bloqueio exclusivo impede um segmento em qualquer instância da classe de executar o `SyncLock` bloquear enquanto qualquer outro segmento o estiver executando.</span><span class="sxs-lookup"><span data-stu-id="2b594-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="2b594-132">Isso protege os dados que são compartilhados entre todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="2b594-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="2b594-133">Se `lockobject` é uma variável de instância (não `Shared`), o bloqueio impede que um thread em execução na instância atual execute o `SyncLock` bloco ao mesmo tempo que outro segmento na mesma instância.</span><span class="sxs-lookup"><span data-stu-id="2b594-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="2b594-134">Isso protege os dados mantidos pela instância individual.</span><span class="sxs-lookup"><span data-stu-id="2b594-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="2b594-135">Aquisição e liberação.</span><span class="sxs-lookup"><span data-stu-id="2b594-135">Acquisition and Release.</span></span> <span data-ttu-id="2b594-136">A `SyncLock` bloco se comporta como um `Try...Finally` em que o `Try` bloco adquire um bloqueio exclusivo no `lockobject` e `Finally` bloco libera.</span><span class="sxs-lookup"><span data-stu-id="2b594-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="2b594-137">Por isso, o `SyncLock` bloco garante a liberação do bloqueio, não importa como você sai do bloco.</span><span class="sxs-lookup"><span data-stu-id="2b594-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="2b594-138">Isso é verdadeiro mesmo no caso de uma exceção não tratada.</span><span class="sxs-lookup"><span data-stu-id="2b594-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="2b594-139">Chamadas de estrutura.</span><span class="sxs-lookup"><span data-stu-id="2b594-139">Framework Calls.</span></span> <span data-ttu-id="2b594-140">O `SyncLock` bloco adquire e libera o bloqueio exclusivo chamando o `Enter` e `Exit` métodos do `Monitor` classe o <xref:System.Threading>namespace.</xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="2b594-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="2b594-141">Práticas de programação</span><span class="sxs-lookup"><span data-stu-id="2b594-141">Programming Practices</span></span>  
 <span data-ttu-id="2b594-142">O `lockobject` expressão sempre deve avaliar a um objeto que pertence à sua classe exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="2b594-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="2b594-143">Você deve declarar uma `Private` variável de objeto para proteger dados pertencentes à instância atual, ou um `Private Shared` variável de objeto para proteger dados comuns a todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="2b594-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="2b594-144">Você não deve usar o `Me` palavra-chave para fornecer um bloqueio de objeto, por exemplo, dados.</span><span class="sxs-lookup"><span data-stu-id="2b594-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="2b594-145">Se o código externo à sua classe tem uma referência a uma instância de sua classe, eles podem usar essa referência como um objeto de bloqueio para um `SyncLock` bloco completamente diferente do seu, protegendo dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="2b594-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="2b594-146">Dessa maneira, sua classe e a outra classe podem impedir entre si de executar seus relacionado `SyncLock` blocos.</span><span class="sxs-lookup"><span data-stu-id="2b594-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="2b594-147">Da mesma forma, o bloqueio em uma cadeia de caracteres pode ser problemático porque qualquer outro código no processo usando a mesma cadeia de caracteres irá compartilhar o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="2b594-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="2b594-148">Você também não deve usar o `Me.GetType` método para fornecer um objeto de bloqueio para dados compartilhados.</span><span class="sxs-lookup"><span data-stu-id="2b594-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="2b594-149">Isso ocorre porque `GetType` sempre retorna a mesma `Type` objeto para um determinado nome de classe.</span><span class="sxs-lookup"><span data-stu-id="2b594-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="2b594-150">O código externo pode chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando.</span><span class="sxs-lookup"><span data-stu-id="2b594-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="2b594-151">Isso resultaria nas duas classes impedindo uma a outra de suas `SyncLock` blocos.</span><span class="sxs-lookup"><span data-stu-id="2b594-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2b594-152">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2b594-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="2b594-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b594-153">Description</span></span>  
 <span data-ttu-id="2b594-154">O exemplo a seguir mostra uma classe que mantém uma lista simple de mensagens.</span><span class="sxs-lookup"><span data-stu-id="2b594-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="2b594-155">Ela armazena as mensagens em uma matriz e o último elemento da matriz usado em uma variável.</span><span class="sxs-lookup"><span data-stu-id="2b594-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="2b594-156">O `addAnotherMessage` procedimento incrementa o último elemento e armazena a nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b594-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="2b594-157">Essas duas operações são protegidas pelo `SyncLock` e `End SyncLock` instruções, porque depois que o último elemento foi incrementado, a nova mensagem deve ser armazenada antes que qualquer outro segmento possa incrementar o último elemento novamente.</span><span class="sxs-lookup"><span data-stu-id="2b594-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="2b594-158">Se o `simpleMessageList` classe compartilhados uma lista de mensagens entre todas as suas instâncias, as variáveis `messagesList` e `messagesLast` deve ser declarado como `Shared`.</span><span class="sxs-lookup"><span data-stu-id="2b594-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="2b594-159">Nesse caso, a variável `messagesLock` também deve ser `Shared`, para que haja um único objeto de bloqueio usado por cada instância.</span><span class="sxs-lookup"><span data-stu-id="2b594-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2b594-160">Código</span><span class="sxs-lookup"><span data-stu-id="2b594-160">Code</span></span>  
 <span data-ttu-id="2b594-161">[!code-vb[VbVbalrThreading n º&1;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2b594-161">[!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]</span></span>  
  
### <a name="description"></a><span data-ttu-id="2b594-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b594-162">Description</span></span>  
 <span data-ttu-id="2b594-163">O exemplo a seguir usa threads e `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="2b594-163">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="2b594-164">Enquanto o `SyncLock` declaração estiver presente, o bloco de instrução é uma seção crítica e `balance` nunca se torne um número negativo.</span><span class="sxs-lookup"><span data-stu-id="2b594-164">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="2b594-165">Você pode comentar o `SyncLock` e `End SyncLock` instruções para ver o efeito de omitindo o `SyncLock` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="2b594-165">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2b594-166">Código</span><span class="sxs-lookup"><span data-stu-id="2b594-166">Code</span></span>  
 <span data-ttu-id="2b594-167">[!code-vb[VbVbalrThreading&#21;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2b594-167">[!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]</span></span>  
  
### <a name="comments"></a><span data-ttu-id="2b594-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b594-168">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b594-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b594-169">See Also</span></span>  
 <span data-ttu-id="2b594-170"><xref:System.Threading></xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="2b594-170"><xref:System.Threading></span></span>   
 <span data-ttu-id="2b594-171"><xref:System.Threading.Monitor></xref:System.Threading.Monitor></span><span class="sxs-lookup"><span data-stu-id="2b594-171"><xref:System.Threading.Monitor></span></span>   
<span data-ttu-id="2b594-172"> [Sincronização de thread](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4) </span><span class="sxs-lookup"><span data-stu-id="2b594-172"> [Thread Synchronization](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4) </span></span>  
<span data-ttu-id="2b594-173"> [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)</span><span class="sxs-lookup"><span data-stu-id="2b594-173"> [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)</span></span>
