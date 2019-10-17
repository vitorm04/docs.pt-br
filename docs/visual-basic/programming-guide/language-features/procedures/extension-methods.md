---
title: Métodos de extensão (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: d988ab36703bc20e6960d4b8ecc7a476d95ee9bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396009"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="ab085-102">Métodos de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab085-102">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="ab085-103">Os métodos de extensão permitem que os desenvolvedores adicionem funcionalidade personalizada a tipos de dados que já estão definidos sem a criação de um novo tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="ab085-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="ab085-104">Os métodos de extensão possibilitam escrever um método que pode ser chamado como se fosse um método de instância do tipo existente.</span><span class="sxs-lookup"><span data-stu-id="ab085-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab085-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab085-105">Remarks</span></span>

<span data-ttu-id="ab085-106">Um método de extensão pode ser apenas um procedimento `Sub` ou um procedimento `Function`.</span><span class="sxs-lookup"><span data-stu-id="ab085-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="ab085-107">Você não pode definir uma propriedade de extensão, um campo ou um evento.</span><span class="sxs-lookup"><span data-stu-id="ab085-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="ab085-108">Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension>` do namespace <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> e devem ser definidos em um [módulo](../../../language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab085-108">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="ab085-109">Se um método de extensão for definido fora de um módulo, o compilador Visual Basic gerará o erro [BC36551](../../../misc/bc36551.md), "os métodos de extensão podem ser definidos somente em módulos".</span><span class="sxs-lookup"><span data-stu-id="ab085-109">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="ab085-110">O primeiro parâmetro em uma definição de método de extensão especifica o tipo de dados que o método estende.</span><span class="sxs-lookup"><span data-stu-id="ab085-110">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="ab085-111">Quando o método é executado, o primeiro parâmetro é associado à instância do tipo de dados que invoca o método.</span><span class="sxs-lookup"><span data-stu-id="ab085-111">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="ab085-112">O atributo `Extension` só pode ser aplicado a um Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)ou [`Function`](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab085-112">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="ab085-113">Se você aplicá-lo a um `Class` ou a um `Structure`, o compilador Visual Basic gerará o erro [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), o atributo "extensão" poderá ser aplicado somente às declarações "módulo", "sub" ou "função".</span><span class="sxs-lookup"><span data-stu-id="ab085-113">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="ab085-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab085-114">Example</span></span>

<span data-ttu-id="ab085-115">O exemplo a seguir define uma extensão `Print` para o tipo de dados <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab085-115">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="ab085-116">O método usa `Console.WriteLine` para exibir uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ab085-116">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="ab085-117">O parâmetro do método `Print`, `aString`, estabelece que o método estende a classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab085-117">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="ab085-118">Observe que a definição do método de extensão está marcada com o atributo de extensão `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="ab085-118">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="ab085-119">Marcar o módulo no qual o método é definido é opcional, mas cada método de extensão deve ser marcado.</span><span class="sxs-lookup"><span data-stu-id="ab085-119">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="ab085-120"><xref:System.Runtime.CompilerServices> deve ser importado para acessar o atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-120"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="ab085-121">Os métodos de extensão podem ser declarados somente dentro de módulos.</span><span class="sxs-lookup"><span data-stu-id="ab085-121">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="ab085-122">Normalmente, o módulo no qual um método de extensão é definido não é o mesmo módulo que aquele em que ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="ab085-122">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="ab085-123">Em vez disso, o módulo que contém o método de extensão é importado, se precisar, para colocá-lo no escopo.</span><span class="sxs-lookup"><span data-stu-id="ab085-123">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="ab085-124">Depois que o módulo que contém `Print` estiver no escopo, o método poderá ser chamado como se fosse um método de instância comum que não aceite nenhum argumento, como `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="ab085-124">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="ab085-125">O exemplo a seguir, `PrintAndPunctuate`, também é uma extensão para <xref:System.String>, desta vez definido com dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ab085-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="ab085-126">O primeiro parâmetro, `aString`, estabelece que o método de extensão estende <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab085-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="ab085-127">O segundo parâmetro, `punc`, deve ser uma cadeia de caracteres de sinais de pontuação que é passada como um argumento quando o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="ab085-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="ab085-128">O método exibe a cadeia de caracteres seguida pelas marcas de pontuação.</span><span class="sxs-lookup"><span data-stu-id="ab085-128">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="ab085-129">O método é chamado enviando em um argumento de cadeia de caracteres para `punc`: `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="ab085-129">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="ab085-130">O exemplo a seguir mostra `Print` e `PrintAndPunctuate` definidos e chamados.</span><span class="sxs-lookup"><span data-stu-id="ab085-130">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="ab085-131"><xref:System.Runtime.CompilerServices> é importado no módulo de definição para habilitar o acesso ao atributo de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-131"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="ab085-132">Em seguida, os métodos de extensão são trazidos para o escopo e chamados:</span><span class="sxs-lookup"><span data-stu-id="ab085-132">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="ab085-133">Tudo o que é necessário para poder executar esses ou métodos de extensão semelhantes é que eles estão no escopo.</span><span class="sxs-lookup"><span data-stu-id="ab085-133">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="ab085-134">Se o módulo que contém um método de extensão estiver no escopo, ele ficará visível no IntelliSense e poderá ser chamado como se fosse um método de instância comum.</span><span class="sxs-lookup"><span data-stu-id="ab085-134">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="ab085-135">Observe que, quando os métodos são invocados, nenhum argumento é enviado para o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ab085-135">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="ab085-136">O parâmetro `aString` nas definições do método anterior está associado a `example`, a instância de `String` que as chama.</span><span class="sxs-lookup"><span data-stu-id="ab085-136">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="ab085-137">O compilador usará `example` como o argumento enviado para o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="ab085-137">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="ab085-138">Se um método de extensão for chamado para um objeto definido como `Nothing`, o método de extensão será executado.</span><span class="sxs-lookup"><span data-stu-id="ab085-138">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="ab085-139">Isso não se aplica a métodos de instância comuns.</span><span class="sxs-lookup"><span data-stu-id="ab085-139">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="ab085-140">Você pode verificar explicitamente o `Nothing` no método de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-140">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="ab085-141">Tipos que podem ser estendidos</span><span class="sxs-lookup"><span data-stu-id="ab085-141">Types that can be extended</span></span>

<span data-ttu-id="ab085-142">Você pode definir um método de extensão na maioria dos tipos que podem ser representados em uma Visual Basic lista de parâmetros, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab085-142">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="ab085-143">Classes (tipos de referência)</span><span class="sxs-lookup"><span data-stu-id="ab085-143">Classes (reference types)</span></span>
- <span data-ttu-id="ab085-144">Estruturas (tipos de valor)</span><span class="sxs-lookup"><span data-stu-id="ab085-144">Structures (value types)</span></span>
- <span data-ttu-id="ab085-145">Interfaces</span><span class="sxs-lookup"><span data-stu-id="ab085-145">Interfaces</span></span>
- <span data-ttu-id="ab085-146">Delegados</span><span class="sxs-lookup"><span data-stu-id="ab085-146">Delegates</span></span>
- <span data-ttu-id="ab085-147">Argumentos ByRef e ByVal</span><span class="sxs-lookup"><span data-stu-id="ab085-147">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="ab085-148">Parâmetros de método genérico</span><span class="sxs-lookup"><span data-stu-id="ab085-148">Generic method parameters</span></span>
- <span data-ttu-id="ab085-149">Matrizes</span><span class="sxs-lookup"><span data-stu-id="ab085-149">Arrays</span></span>

<span data-ttu-id="ab085-150">Como o primeiro parâmetro especifica o tipo de dados que o método de extensão estende, ele é necessário e não pode ser opcional.</span><span class="sxs-lookup"><span data-stu-id="ab085-150">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="ab085-151">Por esse motivo, parâmetros `Optional` e parâmetros `ParamArray` não podem ser o primeiro parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ab085-151">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="ab085-152">Os métodos de extensão não são considerados na associação tardia.</span><span class="sxs-lookup"><span data-stu-id="ab085-152">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="ab085-153">No exemplo a seguir, a instrução `anObject.PrintMe()` gera uma exceção <xref:System.MissingMemberException>, a mesma exceção que você veria se a segunda definição de método de extensão @no__t 2 fosse excluída.</span><span class="sxs-lookup"><span data-stu-id="ab085-153">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="ab085-154">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="ab085-154">Best practices</span></span>

<span data-ttu-id="ab085-155">Os métodos de extensão fornecem uma maneira conveniente e eficiente de estender um tipo existente.</span><span class="sxs-lookup"><span data-stu-id="ab085-155">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="ab085-156">No entanto, para usá-los com êxito, há alguns pontos a serem considerados.</span><span class="sxs-lookup"><span data-stu-id="ab085-156">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="ab085-157">Essas considerações se aplicam principalmente a autores de bibliotecas de classes, mas podem afetar qualquer aplicativo que use métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-157">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="ab085-158">Geralmente, os métodos de extensão que você adiciona aos tipos que não são de sua propriedade são mais vulneráveis do que os métodos de extensão adicionados aos tipos que você controla.</span><span class="sxs-lookup"><span data-stu-id="ab085-158">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="ab085-159">Várias coisas podem ocorrer em classes que não são de sua propriedade que podem interferir nos métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-159">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="ab085-160">Se existir algum membro de instância acessível que tenha uma assinatura compatível com os argumentos na instrução de chamada, sem conversões redutoras necessárias do argumento para o parâmetro, o método de instância será usado em preferência para qualquer método de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-160">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="ab085-161">Portanto, se um método de instância apropriado for adicionado a uma classe em algum momento, um membro de extensão existente que você depende poderá se tornar inacessível.</span><span class="sxs-lookup"><span data-stu-id="ab085-161">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="ab085-162">O autor de um método de extensão não pode impedir que outros programadores gravem métodos de extensão conflitantes que possam ter precedência sobre a extensão original.</span><span class="sxs-lookup"><span data-stu-id="ab085-162">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="ab085-163">Você pode melhorar a robustez colocando métodos de extensão em seu próprio namespace.</span><span class="sxs-lookup"><span data-stu-id="ab085-163">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="ab085-164">Os consumidores da sua biblioteca podem, então, incluir um namespace ou excluí-lo ou selecionar entre namespaces, separadamente do restante da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="ab085-164">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="ab085-165">Pode ser mais seguro estender interfaces do que estender classes, especialmente se você não possuir a interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="ab085-165">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="ab085-166">Uma alteração em uma interface afeta cada classe que a implementa.</span><span class="sxs-lookup"><span data-stu-id="ab085-166">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="ab085-167">Portanto, talvez seja menos provável que o autor adicione ou altere métodos em uma interface.</span><span class="sxs-lookup"><span data-stu-id="ab085-167">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="ab085-168">No entanto, se uma classe implementar duas interfaces que têm métodos de extensão com a mesma assinatura, nenhum método de extensão será visível.</span><span class="sxs-lookup"><span data-stu-id="ab085-168">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="ab085-169">Estenda o tipo mais específico que você pode.</span><span class="sxs-lookup"><span data-stu-id="ab085-169">Extend the most specific type you can.</span></span> <span data-ttu-id="ab085-170">Em uma hierarquia de tipos, se você selecionar um tipo do qual muitos outros tipos são derivados, haverá camadas de possibilidades para a introdução de métodos de instância ou outros métodos de extensão que possam interferir com o seu.</span><span class="sxs-lookup"><span data-stu-id="ab085-170">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="ab085-171">Métodos de extensão, métodos de instância e propriedades</span><span class="sxs-lookup"><span data-stu-id="ab085-171">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="ab085-172">Quando um método de instância no escopo tem uma assinatura que é compatível com os argumentos de uma instrução de chamada, o método de instância é escolhido de preferência para qualquer método de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-172">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="ab085-173">O método de instância tem precedência mesmo se o método de extensão for uma correspondência melhor.</span><span class="sxs-lookup"><span data-stu-id="ab085-173">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="ab085-174">No exemplo a seguir, `ExampleClass` contém um método de instância chamado `ExampleMethod` que tem um parâmetro do tipo `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ab085-174">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="ab085-175">O método de extensão `ExampleMethod` estende `ExampleClass` e tem um parâmetro do tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="ab085-175">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="ab085-176">A primeira chamada para `ExampleMethod` no código a seguir chama o método de extensão, porque `arg1` é `Long` e é compatível apenas com o parâmetro `Long` no método de extensão.</span><span class="sxs-lookup"><span data-stu-id="ab085-176">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="ab085-177">A segunda chamada para `ExampleMethod` tem um argumento `Integer`, `arg2` e chama o método de instância.</span><span class="sxs-lookup"><span data-stu-id="ab085-177">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="ab085-178">Agora inverta os tipos de dados dos parâmetros nos dois métodos:</span><span class="sxs-lookup"><span data-stu-id="ab085-178">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="ab085-179">Desta vez, o código em `Main` chama o método de instância duas vezes.</span><span class="sxs-lookup"><span data-stu-id="ab085-179">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="ab085-180">Isso ocorre porque `arg1` e `arg2` têm uma conversão de ampliação para `Long`, e o método de instância tem precedência sobre o método de extensão em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="ab085-180">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="ab085-181">Portanto, um método de extensão não pode substituir um método de instância existente.</span><span class="sxs-lookup"><span data-stu-id="ab085-181">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="ab085-182">No entanto, quando um método de extensão tem o mesmo nome que um método de instância, mas as assinaturas não entram em conflito, ambos os métodos podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="ab085-182">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="ab085-183">Por exemplo, se a classe `ExampleClass` contiver um método chamado `ExampleMethod` que não usa argumentos, os métodos de extensão com o mesmo nome, mas assinaturas diferentes, serão permitidos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ab085-183">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="ab085-184">A saída desse código é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="ab085-184">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="ab085-185">A situação é mais simples com propriedades: se um método de extensão tiver o mesmo nome que uma propriedade da classe que estende, o método de extensão não será visível e não poderá ser acessado.</span><span class="sxs-lookup"><span data-stu-id="ab085-185">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="ab085-186">Precedência do método de extensão</span><span class="sxs-lookup"><span data-stu-id="ab085-186">Extension method precedence</span></span>

<span data-ttu-id="ab085-187">Quando dois métodos de extensão que têm assinaturas idênticas estiverem no escopo e acessíveis, aquele com maior precedência será invocado.</span><span class="sxs-lookup"><span data-stu-id="ab085-187">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="ab085-188">A precedência de um método de extensão é baseada no mecanismo usado para colocar o método no escopo.</span><span class="sxs-lookup"><span data-stu-id="ab085-188">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="ab085-189">A lista a seguir mostra a hierarquia de precedência, da mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="ab085-189">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="ab085-190">Métodos de extensão definidos dentro do módulo atual.</span><span class="sxs-lookup"><span data-stu-id="ab085-190">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="ab085-191">Métodos de extensão definidos dentro de tipos de dados no namespace atual ou qualquer um de seus pais, com namespaces filho com precedência maior do que namespaces pai.</span><span class="sxs-lookup"><span data-stu-id="ab085-191">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="ab085-192">Métodos de extensão definidos dentro de qualquer tipo importado no arquivo atual.</span><span class="sxs-lookup"><span data-stu-id="ab085-192">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="ab085-193">Métodos de extensão definidos dentro de qualquer importação de namespace no arquivo atual.</span><span class="sxs-lookup"><span data-stu-id="ab085-193">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="ab085-194">Métodos de extensão definidos dentro de qualquer importação de tipo de nível de projeto.</span><span class="sxs-lookup"><span data-stu-id="ab085-194">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="ab085-195">Métodos de extensão definidos dentro de qualquer importação de namespace em nível de projeto.</span><span class="sxs-lookup"><span data-stu-id="ab085-195">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="ab085-196">Se a precedência não resolver a ambiguidade, você poderá usar o nome totalmente qualificado para especificar o método que está chamando.</span><span class="sxs-lookup"><span data-stu-id="ab085-196">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="ab085-197">Se o método `Print` no exemplo anterior for definido em um módulo denominado `StringExtensions`, o nome totalmente qualificado será `StringExtensions.Print(example)` em vez de `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="ab085-197">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab085-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab085-198">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="ab085-199">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="ab085-199">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="ab085-200">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="ab085-200">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="ab085-201">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="ab085-201">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ab085-202">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="ab085-202">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="ab085-203">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab085-203">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="ab085-204">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="ab085-204">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="ab085-205">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab085-205">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
