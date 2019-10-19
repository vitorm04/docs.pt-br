---
title: Instrução SyncLock (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: e981ee727b66ecda392014fd3ee8ca6f1526cd2e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578895"
---
# <a name="synclock-statement"></a><span data-ttu-id="b43ca-102">Instrução SyncLock</span><span class="sxs-lookup"><span data-stu-id="b43ca-102">SyncLock Statement</span></span>
<span data-ttu-id="b43ca-103">Adquire um bloqueio exclusivo para um bloco de instrução antes de executar o bloco.</span><span class="sxs-lookup"><span data-stu-id="b43ca-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b43ca-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="b43ca-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b43ca-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="b43ca-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b43ca-106">Required.</span></span> <span data-ttu-id="b43ca-107">Expressão que é avaliada como uma referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="b43ca-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="b43ca-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b43ca-108">Optional.</span></span> <span data-ttu-id="b43ca-109">Bloco de instruções que devem ser executadas quando o bloqueio é adquirido.</span><span class="sxs-lookup"><span data-stu-id="b43ca-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="b43ca-110">Encerra um bloco de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b43ca-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b43ca-111">Remarks</span></span>  
 <span data-ttu-id="b43ca-112">A instrução `SyncLock` garante que vários threads não executem o bloco de instruções ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="b43ca-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="b43ca-113">`SyncLock` impede que cada thread entre no bloco até que nenhum outro thread o execute.</span><span class="sxs-lookup"><span data-stu-id="b43ca-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="b43ca-114">O uso mais comum de `SyncLock` é proteger os dados de serem atualizados por mais de um thread simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="b43ca-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="b43ca-115">Se as instruções que manipulam os dados devem ir para conclusão sem interrupção, coloque-as dentro de um bloco de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="b43ca-116">Um bloco de instruções protegido por um bloqueio exclusivo às vezes é chamado de *seção crítica*.</span><span class="sxs-lookup"><span data-stu-id="b43ca-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b43ca-117">Regras</span><span class="sxs-lookup"><span data-stu-id="b43ca-117">Rules</span></span>  
  
- <span data-ttu-id="b43ca-118">Ramificação.</span><span class="sxs-lookup"><span data-stu-id="b43ca-118">Branching.</span></span> <span data-ttu-id="b43ca-119">Não é possível ramificar em um bloco de `SyncLock` de fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="b43ca-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="b43ca-120">Bloquear valor do objeto.</span><span class="sxs-lookup"><span data-stu-id="b43ca-120">Lock Object Value.</span></span> <span data-ttu-id="b43ca-121">O valor de `lockobject` não pode ser `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="b43ca-122">Você deve criar o objeto de bloqueio antes de usá-lo em uma instrução `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="b43ca-123">Você não pode alterar o valor de `lockobject` ao executar um bloco de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="b43ca-124">O mecanismo requer que o objeto de bloqueio permaneça inalterado.</span><span class="sxs-lookup"><span data-stu-id="b43ca-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="b43ca-125">Você não pode usar o operador [Await](../../../visual-basic/language-reference/operators/await-operator.md) em um bloco de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b43ca-126">Comportamento</span><span class="sxs-lookup"><span data-stu-id="b43ca-126">Behavior</span></span>  
  
- <span data-ttu-id="b43ca-127">Mecanismo.</span><span class="sxs-lookup"><span data-stu-id="b43ca-127">Mechanism.</span></span> <span data-ttu-id="b43ca-128">Quando um thread alcança a instrução `SyncLock`, ele avalia a expressão de `lockobject` e suspende a execução até que adquira um bloqueio exclusivo no objeto retornado pela expressão.</span><span class="sxs-lookup"><span data-stu-id="b43ca-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="b43ca-129">Quando outro thread alcança a instrução `SyncLock`, ele não adquire um bloqueio até que o primeiro thread execute a instrução `End SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="b43ca-130">Dados protegidos.</span><span class="sxs-lookup"><span data-stu-id="b43ca-130">Protected Data.</span></span> <span data-ttu-id="b43ca-131">Se `lockobject` for uma variável `Shared`, o bloqueio exclusivo impedirá que um thread em qualquer instância da classe execute o bloco de `SyncLock` enquanto qualquer outro thread estiver executando-o.</span><span class="sxs-lookup"><span data-stu-id="b43ca-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="b43ca-132">Isso protege os dados compartilhados entre todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="b43ca-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="b43ca-133">Se `lockobject` for uma variável de instância (não `Shared`), o bloqueio impedirá que um thread em execução na instância atual execute o bloco de `SyncLock` ao mesmo tempo que outro thread na mesma instância.</span><span class="sxs-lookup"><span data-stu-id="b43ca-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="b43ca-134">Isso protege os dados mantidos pela instância individual.</span><span class="sxs-lookup"><span data-stu-id="b43ca-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="b43ca-135">Aquisição e versão.</span><span class="sxs-lookup"><span data-stu-id="b43ca-135">Acquisition and Release.</span></span> <span data-ttu-id="b43ca-136">Um bloco de `SyncLock` se comporta como uma construção de `Try...Finally` na qual o bloco de `Try` adquire um bloqueio exclusivo em `lockobject` e o bloco de `Finally` o libera.</span><span class="sxs-lookup"><span data-stu-id="b43ca-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="b43ca-137">Por isso, o bloqueio de `SyncLock` garante a liberação do bloqueio, independentemente de como você sai do bloco.</span><span class="sxs-lookup"><span data-stu-id="b43ca-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="b43ca-138">Isso é verdadeiro mesmo no caso de uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="b43ca-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="b43ca-139">Chamadas à estrutura.</span><span class="sxs-lookup"><span data-stu-id="b43ca-139">Framework Calls.</span></span> <span data-ttu-id="b43ca-140">O bloco de `SyncLock` adquire e libera o bloqueio exclusivo chamando os métodos `Enter` e `Exit` da classe `Monitor` no namespace <xref:System.Threading>.</span><span class="sxs-lookup"><span data-stu-id="b43ca-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="b43ca-141">Práticas de programação</span><span class="sxs-lookup"><span data-stu-id="b43ca-141">Programming Practices</span></span>  
 <span data-ttu-id="b43ca-142">A expressão de `lockobject` sempre deve ser avaliada como um objeto que pertence exclusivamente à sua classe.</span><span class="sxs-lookup"><span data-stu-id="b43ca-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="b43ca-143">Você deve declarar uma variável de objeto `Private` para proteger os dados pertencentes à instância atual ou uma variável de objeto `Private Shared` para proteger os dados comuns a todas as instâncias.</span><span class="sxs-lookup"><span data-stu-id="b43ca-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="b43ca-144">Você não deve usar a palavra-chave `Me` para fornecer um objeto de bloqueio para dados de instância.</span><span class="sxs-lookup"><span data-stu-id="b43ca-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="b43ca-145">Se o código externo à sua classe tiver uma referência a uma instância da sua classe, ele poderá usar essa referência como um objeto de bloqueio para um bloco de `SyncLock` completamente diferente do seu, protegendo dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="b43ca-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="b43ca-146">Dessa forma, sua classe e a outra classe podem impedir que uma da outra execute seus blocos de `SyncLock` não relacionados.</span><span class="sxs-lookup"><span data-stu-id="b43ca-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="b43ca-147">De maneira semelhante, o bloqueio em uma cadeia de caracteres pode ser problemático, pois qualquer outro código no processo que usa a mesma cadeia de caracteres compartilhará o mesmo bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b43ca-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="b43ca-148">Você também não deve usar o método `Me.GetType` para fornecer um objeto de bloqueio para dados compartilhados.</span><span class="sxs-lookup"><span data-stu-id="b43ca-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="b43ca-149">Isso ocorre porque `GetType` sempre retorna o mesmo objeto `Type` para um determinado nome de classe.</span><span class="sxs-lookup"><span data-stu-id="b43ca-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="b43ca-150">O código externo pode chamar `GetType` em sua classe e obter o mesmo objeto de bloqueio que você está usando.</span><span class="sxs-lookup"><span data-stu-id="b43ca-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="b43ca-151">Isso resultaria em duas classes bloqueando-as a partir de seus blocos de `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b43ca-152">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b43ca-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="b43ca-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="b43ca-153">Description</span></span>  
 <span data-ttu-id="b43ca-154">O exemplo a seguir mostra uma classe que mantém uma lista simples de mensagens.</span><span class="sxs-lookup"><span data-stu-id="b43ca-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="b43ca-155">Ele contém as mensagens em uma matriz e o último elemento usado dessa matriz em uma variável.</span><span class="sxs-lookup"><span data-stu-id="b43ca-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="b43ca-156">O procedimento `addAnotherMessage` incrementa o último elemento e armazena a nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="b43ca-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="b43ca-157">Essas duas operações são protegidas pelas instruções `SyncLock` e `End SyncLock`, porque depois que o último elemento for incrementado, a nova mensagem deverá ser armazenada antes que qualquer outro thread possa incrementar o último elemento novamente.</span><span class="sxs-lookup"><span data-stu-id="b43ca-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="b43ca-158">Se a classe `simpleMessageList` compartilhada uma lista de mensagens entre todas as suas instâncias, as variáveis `messagesList` e `messagesLast` seriam declaradas como `Shared`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="b43ca-159">Nesse caso, a variável `messagesLock` também deve ser `Shared`, para que haja um único objeto de bloqueio usado por cada instância.</span><span class="sxs-lookup"><span data-stu-id="b43ca-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b43ca-160">Código</span><span class="sxs-lookup"><span data-stu-id="b43ca-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="b43ca-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="b43ca-161">Description</span></span>  
 <span data-ttu-id="b43ca-162">O exemplo a seguir usa threads e `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="b43ca-163">Contanto que a instrução de `SyncLock` esteja presente, o bloco de instrução é uma seção crítica e `balance` nunca se torna um número negativo.</span><span class="sxs-lookup"><span data-stu-id="b43ca-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="b43ca-164">Você pode comentar as instruções `SyncLock` e `End SyncLock` para ver o efeito de sair da palavra-chave `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b43ca-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b43ca-165">Código</span><span class="sxs-lookup"><span data-stu-id="b43ca-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="b43ca-166">Comentários</span><span class="sxs-lookup"><span data-stu-id="b43ca-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b43ca-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b43ca-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="b43ca-168">Visão geral dos primitivos de sincronização</span><span class="sxs-lookup"><span data-stu-id="b43ca-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
