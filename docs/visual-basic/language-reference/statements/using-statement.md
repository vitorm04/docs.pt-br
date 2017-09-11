---
title: "Instrução using (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.using
dev_langs:
- VB
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
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
ms.openlocfilehash: efd5eec76a972b89c7b42d56a6564f2edf1da56a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="57b1c-102">Instrução Using (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57b1c-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="57b1c-103">Declara o início de uma `Using` bloquear e opcionalmente adquire os recursos do sistema que controla o bloco.</span><span class="sxs-lookup"><span data-stu-id="57b1c-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57b1c-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="57b1c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="57b1c-105">Parts</span></span>  
  
|<span data-ttu-id="57b1c-106">Termo</span><span class="sxs-lookup"><span data-stu-id="57b1c-106">Term</span></span>|<span data-ttu-id="57b1c-107">Definição</span><span class="sxs-lookup"><span data-stu-id="57b1c-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="57b1c-108">Necessário se você não fornecer `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="57b1c-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="57b1c-109">Lista de um ou mais recursos do sistema que este `Using` bloquear controles, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="57b1c-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="57b1c-110">Necessário se você não fornecer `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="57b1c-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="57b1c-111">Variável ou expressão referindo-se a um recurso do sistema controlado por este `Using` bloco.</span><span class="sxs-lookup"><span data-stu-id="57b1c-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="57b1c-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="57b1c-112">Optional.</span></span> <span data-ttu-id="57b1c-113">Bloco de instruções que o `Using` bloco é executado.</span><span class="sxs-lookup"><span data-stu-id="57b1c-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="57b1c-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57b1c-114">Required.</span></span> <span data-ttu-id="57b1c-115">Finaliza a definição de `Using` bloco e descarta todos os recursos que ele controla.</span><span class="sxs-lookup"><span data-stu-id="57b1c-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="57b1c-116">Cada recurso do `resourcelist` parte tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="57b1c-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="57b1c-117">-ou-</span><span class="sxs-lookup"><span data-stu-id="57b1c-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="57b1c-118">Partes de resourcelist</span><span class="sxs-lookup"><span data-stu-id="57b1c-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="57b1c-119">Termo</span><span class="sxs-lookup"><span data-stu-id="57b1c-119">Term</span></span>|<span data-ttu-id="57b1c-120">Definição</span><span class="sxs-lookup"><span data-stu-id="57b1c-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="57b1c-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57b1c-121">Required.</span></span> <span data-ttu-id="57b1c-122">Variável de referência que se refere a um recurso do sistema que o `Using` bloquear controles.</span><span class="sxs-lookup"><span data-stu-id="57b1c-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="57b1c-123">Necessário se o `Using` instrução adquire o recurso.</span><span class="sxs-lookup"><span data-stu-id="57b1c-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="57b1c-124">Se você já tiver adquirido o recurso, use a segunda sintaxe alternativa.</span><span class="sxs-lookup"><span data-stu-id="57b1c-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="57b1c-125">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57b1c-125">Required.</span></span> <span data-ttu-id="57b1c-126">A classe do recurso.</span><span class="sxs-lookup"><span data-stu-id="57b1c-126">The class of the resource.</span></span> <span data-ttu-id="57b1c-127">A classe deve implementar o <xref:System.IDisposable>interface.</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="57b1c-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="57b1c-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="57b1c-128">Optional.</span></span> <span data-ttu-id="57b1c-129">Lista de argumentos que você está passando para o construtor para criar uma instância de `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="57b1c-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="57b1c-130">Consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="57b1c-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="57b1c-131">Necessário.</span><span class="sxs-lookup"><span data-stu-id="57b1c-131">Required.</span></span> <span data-ttu-id="57b1c-132">Variável ou expressão referindo-se a um recurso de sistema que satisfaz os requisitos do `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="57b1c-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="57b1c-133">Se você usar a segunda sintaxe alternativa, você deve adquirir o recurso antes de passar o controle para o `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="57b1c-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57b1c-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="57b1c-134">Remarks</span></span>  
 <span data-ttu-id="57b1c-135">Às vezes, seu código requer um recurso não gerenciado, como um identificador de arquivo, um wrapper COM ou uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="57b1c-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="57b1c-136">Um `Using` bloco garante a disposição de um ou mais dos tais recursos quando seu código estiver finalizado com eles.</span><span class="sxs-lookup"><span data-stu-id="57b1c-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="57b1c-137">Isso os torna disponível para outro código usar.</span><span class="sxs-lookup"><span data-stu-id="57b1c-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="57b1c-138">Recursos gerenciados são descartados pelo coletor de lixo do .NET Framework (GC) sem qualquer codificação extra de sua parte.</span><span class="sxs-lookup"><span data-stu-id="57b1c-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="57b1c-139">Não é necessário um `Using` bloco de recursos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="57b1c-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="57b1c-140">No entanto, você ainda pode usar um `Using` bloco para forçar o descarte de um recurso gerenciado em vez de esperar o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="57b1c-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="57b1c-141">Um `Using` bloco tem três partes: aquisição, uso e descarte.</span><span class="sxs-lookup"><span data-stu-id="57b1c-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="57b1c-142">*Aquisição* significa criar uma variável e inicializá-la para se referir ao recurso do sistema.</span><span class="sxs-lookup"><span data-stu-id="57b1c-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="57b1c-143">O `Using` instrução pode adquirir um ou mais recursos, ou você pode adquirir exatamente um recurso antes de inserir o bloco e fornece-lo para o `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="57b1c-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="57b1c-144">Se você fornecer `resourceexpression`, você deve adquirir o recurso antes de passar o controle para o `Using` instrução.</span><span class="sxs-lookup"><span data-stu-id="57b1c-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="57b1c-145">*Uso* significa acessar os recursos e executar ações com eles.</span><span class="sxs-lookup"><span data-stu-id="57b1c-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="57b1c-146">As instruções entre `Using` e `End Using` representam o uso de recursos.</span><span class="sxs-lookup"><span data-stu-id="57b1c-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="57b1c-147">*Disposição* significa chamar o <xref:System.IDisposable.Dispose%2A>método no objeto `resourcename`.</xref:System.IDisposable.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="57b1c-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="57b1c-148">Isso permite que o objeto libere corretamente seus recursos.</span><span class="sxs-lookup"><span data-stu-id="57b1c-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="57b1c-149">O `End Using` instrução libera os recursos sob o `Using` controle bloco de.</span><span class="sxs-lookup"><span data-stu-id="57b1c-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="57b1c-150">Comportamento</span><span class="sxs-lookup"><span data-stu-id="57b1c-150">Behavior</span></span>  
 <span data-ttu-id="57b1c-151">A `Using` bloco se comporta como um `Try`... `Finally` em que o `Try` bloco usa os recursos e o `Finally` libera bloco.</span><span class="sxs-lookup"><span data-stu-id="57b1c-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="57b1c-152">Por isso, o `Using` bloco garante a liberação dos recursos, não importa como você sai do bloco.</span><span class="sxs-lookup"><span data-stu-id="57b1c-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="57b1c-153">Isso é verdadeiro mesmo no caso de uma exceção sem tratamento, exceto <xref:System.StackOverflowException>.</xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="57b1c-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="57b1c-154">O escopo de cada recurso variável adquirido pelo `Using` instrução está limitada ao `Using` bloco.</span><span class="sxs-lookup"><span data-stu-id="57b1c-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="57b1c-155">Se você especificar mais de um recurso de sistema no `Using` instrução, o efeito é o mesmo como se você aninhado `Using` bloqueia uma dentro da outra.</span><span class="sxs-lookup"><span data-stu-id="57b1c-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="57b1c-156">Se `resourcename` é `Nothing`, nenhuma chamada para <xref:System.IDisposable.Dispose%2A>é feita, e nenhuma exceção é lançada.</xref:System.IDisposable.Dispose%2A></span><span class="sxs-lookup"><span data-stu-id="57b1c-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="57b1c-157">Tratamento dentro de um bloco usando de exceções estruturado</span><span class="sxs-lookup"><span data-stu-id="57b1c-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="57b1c-158">Se você precisar manipular uma exceção que pode ocorrer dentro de `Using` bloco, você pode adicionar um arquivo `Try`... `Finally` concluída a ela.</span><span class="sxs-lookup"><span data-stu-id="57b1c-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="57b1c-159">Se você precisar manipular o caso em que o `Using` instrução não for bem-sucedida em adquirir um recurso, você pode testar para ver se `resourcename` é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="57b1c-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="57b1c-160">Tratamento em vez de usar um bloco Using de exceções estruturado</span><span class="sxs-lookup"><span data-stu-id="57b1c-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="57b1c-161">Se você precisar exercer um melhor controle sobre a aquisição dos recursos, ou você precisa de código adicional no `Finally` bloco, você pode reescrever o `Using` bloquear como um `Try`... `Finally` construção.</span><span class="sxs-lookup"><span data-stu-id="57b1c-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="57b1c-162">O exemplo a seguir mostra o esqueleto `Try` e `Using` construções que são equivalentes na aquisição e liberação de `resource`.</span><span class="sxs-lookup"><span data-stu-id="57b1c-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  <span data-ttu-id="57b1c-163">O código dentro de `Using` bloco não deve atribuir o objeto `resourcename` a outra variável.</span><span class="sxs-lookup"><span data-stu-id="57b1c-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="57b1c-164">Quando você sai do `Using` bloco, o recurso é descartado, e a outra variável não pode acessar o recurso para o qual ele aponta.</span><span class="sxs-lookup"><span data-stu-id="57b1c-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57b1c-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57b1c-165">Example</span></span>  
 <span data-ttu-id="57b1c-166">O exemplo a seguir cria um arquivo chamado log. txt e grava duas linhas de texto no arquivo.</span><span class="sxs-lookup"><span data-stu-id="57b1c-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="57b1c-167">O exemplo também lê o mesmo arquivo e exibe as linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="57b1c-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="57b1c-168">Porque o <xref:System.IO.TextWriter>e <xref:System.IO.TextReader>classes implementam a <xref:System.IDisposable>interface, o código pode usar `Using` instruções para garantir que o arquivo é fechado após a gravação e operações de leitura corretamente.</xref:System.IDisposable> </xref:System.IO.TextReader> </xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="57b1c-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 <span data-ttu-id="57b1c-169">[!code-vb[VbVbalrStatements&#50;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="57b1c-169">[!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b1c-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57b1c-170">See Also</span></span>  
 <span data-ttu-id="57b1c-171"><xref:System.IDisposable></xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="57b1c-171"><xref:System.IDisposable></span></span>   
<span data-ttu-id="57b1c-172"> [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span><span class="sxs-lookup"><span data-stu-id="57b1c-172"> [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) </span></span>  
<span data-ttu-id="57b1c-173"> [Como descartar um recurso do sistema](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)</span><span class="sxs-lookup"><span data-stu-id="57b1c-173"> [How to: Dispose of a System Resource](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)</span></span>
