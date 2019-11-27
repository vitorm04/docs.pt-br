---
title: Instrução Using
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352767"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="34887-102">Instrução Using (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34887-102">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="34887-103">Declara o início de um bloco de `Using` e, opcionalmente, adquire os recursos do sistema que o bloco controla.</span><span class="sxs-lookup"><span data-stu-id="34887-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="34887-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34887-104">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="34887-105">Partes</span><span class="sxs-lookup"><span data-stu-id="34887-105">Parts</span></span>

|<span data-ttu-id="34887-106">Termo</span><span class="sxs-lookup"><span data-stu-id="34887-106">Term</span></span>|<span data-ttu-id="34887-107">Definição</span><span class="sxs-lookup"><span data-stu-id="34887-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="34887-108">Necessário se você não fornecer `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="34887-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="34887-109">Lista de um ou mais recursos do sistema que esse `Using` bloquear controles, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="34887-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="34887-110">Necessário se você não fornecer `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="34887-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="34887-111">Variável ou expressão de referência que se refere a um recurso do sistema a ser controlado por este bloco de `Using`.</span><span class="sxs-lookup"><span data-stu-id="34887-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="34887-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="34887-112">Optional.</span></span> <span data-ttu-id="34887-113">Bloco de instruções que o bloco de `Using` é executado.</span><span class="sxs-lookup"><span data-stu-id="34887-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="34887-114">Necessária.</span><span class="sxs-lookup"><span data-stu-id="34887-114">Required.</span></span> <span data-ttu-id="34887-115">Encerra a definição do bloco de `Using` e descarta todos os recursos que ele controla.</span><span class="sxs-lookup"><span data-stu-id="34887-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="34887-116">Cada recurso na parte `resourcelist` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="34887-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="34887-117">- ou -</span><span class="sxs-lookup"><span data-stu-id="34887-117">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="34887-118">Partes da resourceList</span><span class="sxs-lookup"><span data-stu-id="34887-118">resourcelist Parts</span></span>

|<span data-ttu-id="34887-119">Termo</span><span class="sxs-lookup"><span data-stu-id="34887-119">Term</span></span>|<span data-ttu-id="34887-120">Definição</span><span class="sxs-lookup"><span data-stu-id="34887-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="34887-121">Necessária.</span><span class="sxs-lookup"><span data-stu-id="34887-121">Required.</span></span> <span data-ttu-id="34887-122">Variável de referência que se refere a um recurso do sistema que o `Using` bloquear controles.</span><span class="sxs-lookup"><span data-stu-id="34887-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="34887-123">Obrigatório se a instrução `Using` adquire o recurso.</span><span class="sxs-lookup"><span data-stu-id="34887-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="34887-124">Se você já tiver adquirido o recurso, use a segunda sintaxe alternativa.</span><span class="sxs-lookup"><span data-stu-id="34887-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="34887-125">Necessária.</span><span class="sxs-lookup"><span data-stu-id="34887-125">Required.</span></span> <span data-ttu-id="34887-126">A classe do recurso.</span><span class="sxs-lookup"><span data-stu-id="34887-126">The class of the resource.</span></span> <span data-ttu-id="34887-127">A classe deve implementar a interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="34887-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="34887-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="34887-128">Optional.</span></span> <span data-ttu-id="34887-129">Lista de argumentos que você está passando para o construtor para criar uma instância de `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="34887-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="34887-130">Consulte a [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="34887-130">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="34887-131">Necessária.</span><span class="sxs-lookup"><span data-stu-id="34887-131">Required.</span></span> <span data-ttu-id="34887-132">Variável ou expressão referindo-se a um recurso do sistema que atende aos requisitos de `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="34887-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="34887-133">Se você usar a segunda alternativa de sintaxe, deverá adquirir o recurso antes de passar o controle para a instrução `Using`.</span><span class="sxs-lookup"><span data-stu-id="34887-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34887-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="34887-134">Remarks</span></span>

 <span data-ttu-id="34887-135">Às vezes, seu código requer um recurso não gerenciado, como um identificador de arquivo, um wrapper COM ou uma conexão SQL.</span><span class="sxs-lookup"><span data-stu-id="34887-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="34887-136">Um bloco de `Using` garante a eliminação de um ou mais desses recursos quando seu código é concluído com eles.</span><span class="sxs-lookup"><span data-stu-id="34887-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="34887-137">Isso os torna disponíveis para uso de outro código.</span><span class="sxs-lookup"><span data-stu-id="34887-137">This makes them available for other code to use.</span></span>

 <span data-ttu-id="34887-138">Os recursos gerenciados são descartados pelo GC (coletor de lixo .NET Framework) sem qualquer codificação extra de sua parte.</span><span class="sxs-lookup"><span data-stu-id="34887-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="34887-139">Você não precisa de um bloco de `Using` para recursos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="34887-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="34887-140">No entanto, você ainda pode usar um bloco de `Using` para forçar a eliminação de um recurso gerenciado em vez de aguardar o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="34887-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="34887-141">Um bloco de `Using` tem três partes: aquisição, uso e alienação.</span><span class="sxs-lookup"><span data-stu-id="34887-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="34887-142">A *aquisição* significa criar uma variável e inicializá-la para se referir ao recurso do sistema.</span><span class="sxs-lookup"><span data-stu-id="34887-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="34887-143">A instrução `Using` pode adquirir um ou mais recursos, ou você pode adquirir exatamente um recurso antes de inserir o bloco e fornecê-lo à instrução `Using`.</span><span class="sxs-lookup"><span data-stu-id="34887-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="34887-144">Se você fornecer `resourceexpression`, deverá adquirir o recurso antes de passar o controle para a instrução `Using`.</span><span class="sxs-lookup"><span data-stu-id="34887-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="34887-145">O *uso* significa acessar os recursos e executar ações com eles.</span><span class="sxs-lookup"><span data-stu-id="34887-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="34887-146">As instruções entre `Using` e `End Using` representam o uso dos recursos.</span><span class="sxs-lookup"><span data-stu-id="34887-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="34887-147">*Alienação* significa chamar o método <xref:System.IDisposable.Dispose%2A> no objeto em `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="34887-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="34887-148">Isso permite que o objeto termine corretamente seus recursos.</span><span class="sxs-lookup"><span data-stu-id="34887-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="34887-149">A instrução `End Using` descarta os recursos sob o controle do bloco de `Using`.</span><span class="sxs-lookup"><span data-stu-id="34887-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="34887-150">Comportamento</span><span class="sxs-lookup"><span data-stu-id="34887-150">Behavior</span></span>

 <span data-ttu-id="34887-151">Um bloco de `Using` se comporta como uma `Try`...`Finally` construção na qual o bloco de `Try` usa os recursos e o bloco de `Finally` descarta-os.</span><span class="sxs-lookup"><span data-stu-id="34887-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="34887-152">Por isso, o bloco de `Using` garante a alienação dos recursos, independentemente de como você sai do bloco.</span><span class="sxs-lookup"><span data-stu-id="34887-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="34887-153">Isso é verdadeiro mesmo no caso de uma exceção sem tratamento, exceto para um <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="34887-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="34887-154">O escopo de cada variável de recurso adquirido pela instrução `Using` é limitado ao bloco de `Using`.</span><span class="sxs-lookup"><span data-stu-id="34887-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="34887-155">Se você especificar mais de um recurso do sistema na instrução `Using`, o efeito será o mesmo que se você tiver aninhado `Using` blocos um dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="34887-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="34887-156">Se `resourcename` for `Nothing`, nenhuma chamada para <xref:System.IDisposable.Dispose%2A> será feita e nenhuma exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="34887-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="34887-157">Manipulação de exceção estruturada dentro de um bloco Using</span><span class="sxs-lookup"><span data-stu-id="34887-157">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="34887-158">Se você precisar manipular uma exceção que pode ocorrer dentro do bloco de `Using`, poderá adicionar uma construção `Try`...`Finally` completa a ela.</span><span class="sxs-lookup"><span data-stu-id="34887-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="34887-159">Se você precisar lidar com o caso em que a instrução `Using` não é bem-sucedida ao adquirir um recurso, você pode testar para ver se `resourcename` está `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="34887-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="34887-160">Manipulação de exceção estruturada em vez de um bloco Using</span><span class="sxs-lookup"><span data-stu-id="34887-160">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="34887-161">Se precisar de um controle mais preciso sobre a aquisição dos recursos ou se precisar de código adicional no bloco de `Finally`, você poderá reescrever o bloco de `Using` como uma construção `Try`...`Finally`.</span><span class="sxs-lookup"><span data-stu-id="34887-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="34887-162">O exemplo a seguir mostra `Try` de esqueleto e construções de `Using` que são equivalentes na aquisição e no descarte de `resource`.</span><span class="sxs-lookup"><span data-stu-id="34887-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

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
> <span data-ttu-id="34887-163">O código dentro do bloco de `Using` não deve atribuir o objeto em `resourcename` a outra variável.</span><span class="sxs-lookup"><span data-stu-id="34887-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="34887-164">Quando você sai do bloco de `Using`, o recurso é Descartado e a outra variável não pode acessar o recurso ao qual ele aponta.</span><span class="sxs-lookup"><span data-stu-id="34887-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="34887-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34887-165">Example</span></span>

 <span data-ttu-id="34887-166">O exemplo a seguir cria um arquivo chamado log. txt e grava duas linhas de texto no arquivo.</span><span class="sxs-lookup"><span data-stu-id="34887-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="34887-167">O exemplo também lê o mesmo arquivo e exibe as linhas de texto:</span><span class="sxs-lookup"><span data-stu-id="34887-167">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="34887-168">Como as classes <xref:System.IO.TextWriter> e <xref:System.IO.TextReader> implementam a interface <xref:System.IDisposable>, o código pode usar instruções `Using` para garantir que o arquivo seja fechado corretamente após as operações de gravação e leitura.</span><span class="sxs-lookup"><span data-stu-id="34887-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="34887-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34887-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="34887-170">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="34887-170">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="34887-171">Como descartar um recurso do sistema</span><span class="sxs-lookup"><span data-stu-id="34887-171">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
