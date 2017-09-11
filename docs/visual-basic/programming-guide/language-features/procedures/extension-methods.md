---
title: "Métodos de extensão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0705929da72bcb3001228a90bbb9d5ba7c248bf7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="a5ff2-102">Métodos de extensão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5ff2-102">Extension Methods (Visual Basic)</span></span>
<span data-ttu-id="a5ff2-103">Métodos de extensão permitem aos desenvolvedores adicionar funcionalidade personalizada para tipos de dados que já foram definidos sem criar um novo tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-103">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="a5ff2-104">Métodos de extensão permitem escrever um método que pode ser chamado como se fosse um método de instância do tipo existente.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-104">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5ff2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5ff2-105">Remarks</span></span>  
 <span data-ttu-id="a5ff2-106">Um método de extensão pode ser apenas um `Sub` procedimento ou uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-106">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="a5ff2-107">Você não pode definir uma propriedade de extensão, o campo ou o evento.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-107">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="a5ff2-108">Todos os métodos de extensão devem ser marcados com o atributo de extensão `<Extension()>` do <xref:System.Runtime.CompilerServices?displayProperty=fullName>namespace.</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a5ff2-108">All extension methods must be marked with the extension attribute `<Extension()>` from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span>  
  
 <span data-ttu-id="a5ff2-109">O primeiro parâmetro em uma definição de método de extensão especifica o tipo de dados o método estende.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-109">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="a5ff2-110">Quando o método for executado, o primeiro parâmetro é associado à instância do tipo de dados que chama o método.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-110">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ff2-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5ff2-111">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a5ff2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5ff2-112">Description</span></span>  
 <span data-ttu-id="a5ff2-113">O exemplo a seguir define uma `Print` extensão para o <xref:System.String>tipo de dados.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a5ff2-113">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="a5ff2-114">Usa o método `Console.WriteLine` para exibir uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-114">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="a5ff2-115">O parâmetro do `Print` método `aString`, estabelece o método estende a <xref:System.String>classe.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a5ff2-115">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>  
  
 <span data-ttu-id="a5ff2-116">[!code-vb[VbVbalrExtensionMethods n º&1;](./codesnippet/VisualBasic/extension-methods_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-116">[!code-vb[VbVbalrExtensionMethods#1](./codesnippet/VisualBasic/extension-methods_1.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-117">Observe que a definição do método de extensão é marcada com o atributo de extensão `<Extension()>`.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-117">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="a5ff2-118">O módulo no qual o método é definido de marcação é opcional, mas cada método de extensão deve ser marcado.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-118">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="a5ff2-119"><xref:System.Runtime.CompilerServices>deve ser importado para acessar o atributo de extensão.</xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="a5ff2-119"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>  
  
 <span data-ttu-id="a5ff2-120">Métodos de extensão podem ser declarados dentro de módulos.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-120">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="a5ff2-121">Normalmente, o módulo no qual é definido um método de extensão não é o mesmo módulo aquele no qual ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-121">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="a5ff2-122">Em vez disso, o módulo que contém o método de extensão é importado, se ele precisa fazer para colocá-lo no escopo.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-122">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="a5ff2-123">Após o módulo que contém `Print` está no escopo, o método pode ser chamado como se fosse um método de instância comum que leva sem argumentos, como `ToUpper`:</span><span class="sxs-lookup"><span data-stu-id="a5ff2-123">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>  
  
 <span data-ttu-id="a5ff2-124">[!code-vb[VbVbalrExtensionMethods n º&2;](./codesnippet/VisualBasic/extension-methods_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-124">[!code-vb[VbVbalrExtensionMethods#2](./codesnippet/VisualBasic/extension-methods_2.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-125">O exemplo a seguir, `PrintAndPunctuate`, também é uma extensão para <xref:System.String>, desta vez, definido com dois parâmetros.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a5ff2-125">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="a5ff2-126">O primeiro parâmetro, `aString`, estabelece o método de extensão estende <xref:System.String>.</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a5ff2-126">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="a5ff2-127">O segundo parâmetro, `punc`, deve ser uma cadeia de caracteres de pontuação que é passada como um argumento quando o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-127">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="a5ff2-128">O método exibe a cadeia de caracteres seguida as marcas de pontuação.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-128">The method displays the string followed by the punctuation marks.</span></span>  
  
 <span data-ttu-id="a5ff2-129">[!code-vb[VbVbalrExtensionMethods n º&3;](./codesnippet/VisualBasic/extension-methods_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-129">[!code-vb[VbVbalrExtensionMethods#3](./codesnippet/VisualBasic/extension-methods_3.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-130">O método é chamado através do envio de um argumento de cadeia de caracteres para `punc`:`example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="a5ff2-130">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>  
  
 <span data-ttu-id="a5ff2-131">A exemplo a seguir mostra `Print` e `PrintAndPunctuate` definidos e chamada.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-131">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="a5ff2-132"><xref:System.Runtime.CompilerServices>é importado no módulo de definição para habilitar o acesso ao atributo de extensão.</xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="a5ff2-132"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a5ff2-133">Código</span><span class="sxs-lookup"><span data-stu-id="a5ff2-133">Code</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="a5ff2-134">Em seguida, os métodos de extensão são trazidos para o escopo e chamados.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-134">Next, the extension methods are brought into scope and called.</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="a5ff2-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5ff2-135">Comments</span></span>  
 <span data-ttu-id="a5ff2-136">Tudo o que é necessário para poder executá-los ou métodos de extensão semelhantes é que eles sejam no escopo.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-136">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="a5ff2-137">Se o módulo que contém um método de extensão estiver no escopo, ele fica visível no IntelliSense e pode ser chamado como se fosse um método de instância comum.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-137">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>  
  
 <span data-ttu-id="a5ff2-138">Observe que quando os métodos são chamados, nenhum argumento é enviado para o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-138">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="a5ff2-139">Parâmetro `aString` no método anterior definições está associado a `example`, a instância de `String` que os chama.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-139">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="a5ff2-140">O compilador usará `example` como o argumento enviado para o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-140">The compiler will use `example` as the argument sent to the first parameter.</span></span>  
  
 <span data-ttu-id="a5ff2-141">Se um método de extensão é chamado de um objeto é definido como `Nothing`, o método de extensão é executado.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-141">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="a5ff2-142">Isso não se aplica aos métodos de instância comum.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-142">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="a5ff2-143">Você pode verificar explicitamente `Nothing` no método de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-143">You can explicitly check for `Nothing` in the extension method.</span></span>  
  
## <a name="types-that-can-be-extended"></a><span data-ttu-id="a5ff2-144">Tipos que podem ser estendidos</span><span class="sxs-lookup"><span data-stu-id="a5ff2-144">Types That Can Be Extended</span></span>  
 <span data-ttu-id="a5ff2-145">Você pode definir um método de extensão na maioria dos tipos que podem ser representados em uma lista de parâmetros do Visual Basic, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a5ff2-145">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>  
  
-   <span data-ttu-id="a5ff2-146">Classes (tipos de referência)</span><span class="sxs-lookup"><span data-stu-id="a5ff2-146">Classes (reference types)</span></span>  
  
-   <span data-ttu-id="a5ff2-147">Estruturas (tipos de valor)</span><span class="sxs-lookup"><span data-stu-id="a5ff2-147">Structures (value types)</span></span>  
  
-   <span data-ttu-id="a5ff2-148">Interfaces</span><span class="sxs-lookup"><span data-stu-id="a5ff2-148">Interfaces</span></span>  
  
-   <span data-ttu-id="a5ff2-149">Delegados</span><span class="sxs-lookup"><span data-stu-id="a5ff2-149">Delegates</span></span>  
  
-   <span data-ttu-id="a5ff2-150">Argumentos ByRef e ByVal</span><span class="sxs-lookup"><span data-stu-id="a5ff2-150">ByRef and ByVal arguments</span></span>  
  
-   <span data-ttu-id="a5ff2-151">Parâmetros de método genérico</span><span class="sxs-lookup"><span data-stu-id="a5ff2-151">Generic method parameters</span></span>  
  
-   <span data-ttu-id="a5ff2-152">Matrizes</span><span class="sxs-lookup"><span data-stu-id="a5ff2-152">Arrays</span></span>  
  
 <span data-ttu-id="a5ff2-153">Como o primeiro parâmetro especifica o tipo de dados que estende o método de extensão, é necessário e não pode ser opcional.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-153">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="a5ff2-154">Por esse motivo, `Optional` parâmetros e `ParamArray` parâmetros não podem ser o primeiro parâmetro na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-154">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>  
  
 <span data-ttu-id="a5ff2-155">Métodos de extensão não são considerados na ligação tardia.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-155">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="a5ff2-156">No exemplo a seguir, a instrução `anObject.PrintMe()` gera um <xref:System.MissingMemberException>exceção, a mesma exceção que você veria se o segundo `PrintMe` definição do método de extensão foram excluídos.</xref:System.MissingMemberException></span><span class="sxs-lookup"><span data-stu-id="a5ff2-156">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>  
  
 <span data-ttu-id="a5ff2-157">[!code-vb[VbVbalrExtensionMethods n º&9;](./codesnippet/VisualBasic/extension-methods_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-157">[!code-vb[VbVbalrExtensionMethods#9](./codesnippet/VisualBasic/extension-methods_4.vb)]</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="a5ff2-158">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="a5ff2-158">Best Practices</span></span>  
 <span data-ttu-id="a5ff2-159">Métodos de extensão fornecem uma maneira poderosa e conveniente de estender um tipo existente.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-159">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="a5ff2-160">No entanto, para usá-las com êxito, há alguns pontos a considerar.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-160">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="a5ff2-161">Essas considerações se aplicam principalmente para autores de bibliotecas de classes, mas eles podem afetar qualquer aplicativo que usa os métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-161">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>  
  
 <span data-ttu-id="a5ff2-162">Mais geralmente, os métodos de extensão que você adicionar a tipos que não possuem são mais vulneráveis que adicionados aos tipos que você controle os métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-162">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="a5ff2-163">Várias coisas podem ocorrer em classes que você não possui e que podem interferir com seus métodos de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-163">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>  
  
-   <span data-ttu-id="a5ff2-164">Se houver qualquer membro de instância acessível tem uma assinatura que é compatível com os argumentos na instrução de chamada, com nenhuma restrição conversões necessárias do argumento para o parâmetro, o método de instância será usado em vez de qualquer método de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-164">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="a5ff2-165">Portanto, se um método de instância apropriado é adicionado a uma classe em algum momento, um membro existente de extensão que você depende pode se tornar inacessível.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-165">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>  
  
-   <span data-ttu-id="a5ff2-166">O autor de um método de extensão não pode impedir que outros programadores escrevendo conflitantes métodos de extensão que podem ter precedência sobre a extensão original.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-166">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>  
  
-   <span data-ttu-id="a5ff2-167">Você pode aumentar a robustez colocando os métodos de extensão em seu próprio namespace.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-167">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="a5ff2-168">Os consumidores de sua biblioteca podem incluir um namespace ou excluí-la ou selecionar entre namespaces, separadamente do restante da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-168">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>  
  
-   <span data-ttu-id="a5ff2-169">Ele pode ser mais seguro estender interfaces que estender as classes, especialmente se você não possui a interface ou classe.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-169">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="a5ff2-170">Uma alteração em uma interface afeta todas as classes que a implementa.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-170">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="a5ff2-171">Portanto, o autor pode ser menos provável adicionar ou alterar os métodos em uma interface.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-171">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="a5ff2-172">No entanto, se uma classe implementa duas interfaces com métodos de extensão com a mesma assinatura, nenhum método de extensão é visível.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-172">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>  
  
-   <span data-ttu-id="a5ff2-173">Estenda o tipo mais específico, que você pode.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-173">Extend the most specific type you can.</span></span> <span data-ttu-id="a5ff2-174">Em uma hierarquia de tipos, se você selecionar um tipo do qual muitos outros tipos são derivados, há camadas de possibilidades para a introdução de métodos de instância ou outros métodos de extensão que podem interferir com as suas.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-174">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>  
  
## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="a5ff2-175">Métodos de extensão, os métodos de instância e propriedades</span><span class="sxs-lookup"><span data-stu-id="a5ff2-175">Extension Methods, Instance Methods, and Properties</span></span>  
 <span data-ttu-id="a5ff2-176">Quando um método de instância no escopo tem uma assinatura compatível com os argumentos de uma instrução de chamada, o método de instância é escolhido em vez de qualquer método de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-176">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="a5ff2-177">O método de instância tem precedência, mesmo se o método de extensão é uma correspondência melhor.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-177">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="a5ff2-178">No exemplo a seguir, `ExampleClass` contém um método de instância chamado `ExampleMethod` que tem um parâmetro do tipo `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-178">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="a5ff2-179">Método de extensão `ExampleMethod` estende `ExampleClass`, e tem um parâmetro do tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-179">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>  
  
 <span data-ttu-id="a5ff2-180">[!code-vb[VbVbalrExtensionMethods n º&4;](./codesnippet/VisualBasic/extension-methods_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-180">[!code-vb[VbVbalrExtensionMethods#4](./codesnippet/VisualBasic/extension-methods_5.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-181">A primeira chamada para `ExampleMethod` no código a seguir chama o método de extensão, como `arg1` é `Long` e é compatível apenas com o `Long` parâmetro no método de extensão.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-181">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="a5ff2-182">A segunda chamada para `ExampleMethod` tem um `Integer` argumento, `arg2`, e chama o método de instância.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-182">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>  
  
 <span data-ttu-id="a5ff2-183">[!code-vb[VbVbalrExtensionMethods n º&5;](./codesnippet/VisualBasic/extension-methods_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-183">[!code-vb[VbVbalrExtensionMethods#5](./codesnippet/VisualBasic/extension-methods_6.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-184">Agora reverte os tipos de dados dos parâmetros nos dois métodos:</span><span class="sxs-lookup"><span data-stu-id="a5ff2-184">Now reverse the data types of the parameters in the two methods:</span></span>  
  
 <span data-ttu-id="a5ff2-185">[!code-vb[VbVbalrExtensionMethods n º&6;](./codesnippet/VisualBasic/extension-methods_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-185">[!code-vb[VbVbalrExtensionMethods#6](./codesnippet/VisualBasic/extension-methods_7.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-186">Dessa vez o código em `Main` chama o método de instância nas duas vezes.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-186">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="a5ff2-187">Isso ocorre porque ambos `arg1` e `arg2` tem uma conversão de ampliação para `Long`, e o método de instância tem precedência sobre o método de extensão em ambos os casos.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-187">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>  
  
 <span data-ttu-id="a5ff2-188">[!code-vb[VbVbalrExtensionMethods&#7;](./codesnippet/VisualBasic/extension-methods_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-188">[!code-vb[VbVbalrExtensionMethods#7](./codesnippet/VisualBasic/extension-methods_8.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-189">Portanto, um método de extensão não pode substituir um método de instância existente.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-189">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="a5ff2-190">No entanto, quando um método de extensão tem o mesmo nome que um método de instância, mas as assinaturas não entrem em conflito, os dois métodos podem ser acessados.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-190">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="a5ff2-191">Por exemplo, se classe `ExampleClass` contém um método chamado `ExampleMethod` que leva sem argumentos, os métodos de extensão com o mesmo nome mas assinaturas diferentes são permitidas, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-191">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>  
  
 <span data-ttu-id="a5ff2-192">[!code-vb[VbVbalrExtensionMethods n º&8;](./codesnippet/VisualBasic/extension-methods_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5ff2-192">[!code-vb[VbVbalrExtensionMethods#8](./codesnippet/VisualBasic/extension-methods_9.vb)]</span></span>  
  
 <span data-ttu-id="a5ff2-193">A saída desse código é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a5ff2-193">The output from this code is as follows:</span></span>  
  
 `Extension method`  
  
 `Instance method`  
  
 <span data-ttu-id="a5ff2-194">A situação é mais simples com propriedades: se um método de extensão tem o mesmo nome que uma propriedade da classe que estende a ele, o método de extensão não estiver visível e não pode ser acessado.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-194">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>  
  
## <a name="extension-method-precedence"></a><span data-ttu-id="a5ff2-195">Precedência do método de extensão</span><span class="sxs-lookup"><span data-stu-id="a5ff2-195">Extension Method Precedence</span></span>  
 <span data-ttu-id="a5ff2-196">Quando dois métodos de extensão possuem assinaturas idênticas estão no escopo e acessível, aquela com a precedência mais alta será invocada.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-196">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="a5ff2-197">Precedência de um método de extensão se baseia o mecanismo usado para trazer o método para o escopo.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-197">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="a5ff2-198">A lista a seguir mostra a hierarquia de precedência, em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-198">The following list shows the precedence hierarchy, from highest to lowest.</span></span>  
  
1.  <span data-ttu-id="a5ff2-199">Métodos de extensão definidos dentro do módulo atual.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-199">Extension methods defined inside the current module.</span></span>  
  
2.  <span data-ttu-id="a5ff2-200">Métodos de extensão definidos nos dados tipos no namespace atual ou qualquer um de seus pais, com os namespaces filho ter precedência maior do que espaços para nome do pai.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-200">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>  
  
3.  <span data-ttu-id="a5ff2-201">Métodos de extensão definidos em imports qualquer tipo no arquivo atual.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-201">Extension methods defined inside any type imports in the current file.</span></span>  
  
4.  <span data-ttu-id="a5ff2-202">Métodos de extensão definidos nas importações de namespace no arquivo atual.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-202">Extension methods defined inside any namespace imports in the current file.</span></span>  
  
5.  <span data-ttu-id="a5ff2-203">Métodos de extensão definidos em qualquer tipo de nível de projeto imports.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-203">Extension methods defined inside any project-level type imports.</span></span>  
  
6.  <span data-ttu-id="a5ff2-204">Métodos de extensão definidos nas importações de namespace de nível de projeto.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-204">Extension methods defined inside any project-level namespace imports.</span></span>  
  
 <span data-ttu-id="a5ff2-205">Se a precedência não resolver a ambiguidade, você pode usar o nome totalmente qualificado para especificar o método que você está chamando.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-205">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="a5ff2-206">Se o `Print` método no exemplo anterior é definido em um módulo denominado `StringExtensions`, o nome totalmente qualificado é `StringExtensions.Print(example)` em vez de `example.Print()`.</span><span class="sxs-lookup"><span data-stu-id="a5ff2-206">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ff2-207">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5ff2-207">See Also</span></span>  
 <span data-ttu-id="a5ff2-208"><xref:System.Runtime.CompilerServices></xref:System.Runtime.CompilerServices></span><span class="sxs-lookup"><span data-stu-id="a5ff2-208"><xref:System.Runtime.CompilerServices></span></span>   
 <span data-ttu-id="a5ff2-209"><xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="a5ff2-209"><xref:System.Runtime.CompilerServices.ExtensionAttribute></span></span>   
<span data-ttu-id="a5ff2-210"> [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="a5ff2-210"> [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
<span data-ttu-id="a5ff2-211"> [Instrução Module](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a5ff2-211"> [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="a5ff2-212"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a5ff2-212"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a5ff2-213"> [Parâmetros opcionais](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a5ff2-213"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="a5ff2-214"> [Matrizes de parâmetros](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="a5ff2-214"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="a5ff2-215"> [Visão geral de atributos](../../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="a5ff2-215"> [Attributes overview](../../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="a5ff2-216"> [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span><span class="sxs-lookup"><span data-stu-id="a5ff2-216"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)</span></span>
