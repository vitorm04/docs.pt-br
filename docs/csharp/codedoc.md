---
title: Documentando seu código com comentários em XML
description: Saiba como documentar seu código com comentários de documentação XML e gerar um arquivo de documentação XML em tempo de compilação.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: e211543a6a5cc5f6f29d8c195492b474eb24a38d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46584065"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="c9aa9-103">Documentando seu código com comentários em XML</span><span class="sxs-lookup"><span data-stu-id="c9aa9-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="c9aa9-104">Comentários em documentação XML são um tipo especial de comentário, adicionados acima da definição de qualquer membro ou tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="c9aa9-105">Eles são especiais porque podem ser processados pelo compilador para gerar um arquivo de documentação XML em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="c9aa9-106">O arquivo XML gerado pelo compilador pode ser distribuído em conjunto com seu assembly .NET para que o Visual Studio e outros IDEs possam usar o IntelliSense para mostrar informações rápidas sobre os tipos ou membros.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="c9aa9-107">Além disso, o arquivo XML pode ser executado por ferramentas como [DocFX](https://dotnet.github.io/docfx/) e [Sandcastle](https://github.com/EWSoftware/SHFB) para gerar sites de referência de API.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="c9aa9-108">Comentários de documentação XML, como todos os outros comentários, são ignorados pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="c9aa9-109">É possível gerar o arquivo XML em tempo de compilação seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="c9aa9-110">Se estiver desenvolvendo um aplicativo com .NET Core da linha de comando, você poderá adicionar um [elemento DocumentationFile](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) à seção `<PropertyGroup>` do arquivo de projeto .csproj.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="c9aa9-111">O seguinte exemplo gera um arquivo XML no diretório do projeto com o mesmo nome de arquivo raiz do assembly:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="c9aa9-112">Você também pode especificar o caminho relativo ou absoluto exato e o nome do arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="c9aa9-113">O exemplo a seguir gera o arquivo XML no mesmo diretório que a versão de depuração de um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="c9aa9-114">Se estiver desenvolvendo um aplicativo usando o Visual Studio, clique com botão direito do mouse no projeto e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="c9aa9-115">Na caixa de diálogo Propriedades, selecione a guia **Build** e marque **Arquivo de documentação XML**.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="c9aa9-116">Também é possível alterar o local em que o compilador grava o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="c9aa9-117">Se você estiver compilando um aplicativo .NET Framework da linha de comando, adicione a [opção do compilador /doc](language-reference/compiler-options/doc-compiler-option.md) durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="c9aa9-118">Comentários de documentação XML usam três barras (`///`) e o corpo do comentário formatado em XML.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="c9aa9-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="c9aa9-120">Passo a passo</span><span class="sxs-lookup"><span data-stu-id="c9aa9-120">Walkthrough</span></span>

<span data-ttu-id="c9aa9-121">Vamos examinar a documentação de uma biblioteca de matemática bastante básica para facilitar a compreensão/contribuição por novos desenvolvedores e facilitar o uso por desenvolvedores de terceiros.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="c9aa9-122">Este é o código para a biblioteca de matemática simples:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="c9aa9-123">A biblioteca de exemplo dá suporte a quatro operações aritméticas principais, `add`, `subtract`, `multiply` e `divide`, nos tipos de dados `int` e `double`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="c9aa9-124">Agora, você quer poder criar um documento de referência de API do seu código para desenvolvedores de terceiros que usam sua biblioteca, mas não têm acesso ao código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="c9aa9-125">Conforme mencionado, marcas de documentação XML anteriores podem ser usadas para fazer isso. Agora, você conhecerá as marcas XML padrão a que o compilador C# dá suporte.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-125">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="c9aa9-126">&lt;summary&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-126">&lt;summary&gt;</span></span>

<span data-ttu-id="c9aa9-127">A marca `<summary>` adiciona informações sucintas sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-127">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="c9aa9-128">Vou demonstrar seu uso adicionando-a à definição de classe `Math` e ao primeiro método `Add`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-128">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="c9aa9-129">Fique à vontade para aplicá-la ao restante de seu código.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-129">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="c9aa9-130">A marca `<summary>` é muito importante e é recomendável inclui-la, porque seu conteúdo é a principal fonte de informações sobre o tipo ou membro no IntelliSense ou em um documento de referência de API.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-130">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="c9aa9-131">&lt;remarks&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-131">&lt;remarks&gt;</span></span>

<span data-ttu-id="c9aa9-132">A marca `<remarks>` complementa as informações sobre tipos ou membros que a marca `<summary>` fornece.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-132">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="c9aa9-133">Neste exemplo, você apenas a adiciona à classe.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-133">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="c9aa9-134">&lt;returns&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-134">&lt;returns&gt;</span></span>

<span data-ttu-id="c9aa9-135">A marca `<returns>` descreve o valor retornado de uma declaração de método.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-135">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="c9aa9-136">Assim como antes, o exemplo a seguir ilustra a marca `<returns>` no primeiro método `Add`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-136">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="c9aa9-137">É possível fazer o mesmo em outros métodos.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-137">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="c9aa9-138">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-138">&lt;value&gt;</span></span>

<span data-ttu-id="c9aa9-139">A marca `<value>` é semelhante à marca `<returns>`, exceto pelo fato de você usá-la para propriedades.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-139">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="c9aa9-140">Supondo que sua biblioteca `Math` tivesse uma propriedade estática chamada `PI`, você usaria essa marca desta forma:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-140">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="c9aa9-141">&lt;example&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-141">&lt;example&gt;</span></span>

<span data-ttu-id="c9aa9-142">Você usa a marca `<example>` para incluir um exemplo em sua documentação XML.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-142">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="c9aa9-143">Isso envolve o uso da marca `<code>` filho.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-143">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="c9aa9-144">A marca `code` preserva quebras de linha e recuos para exemplos mais longos.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-144">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="c9aa9-145">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-145">&lt;para&gt;</span></span>

<span data-ttu-id="c9aa9-146">Você usa a marca `<para>` para formatar o conteúdo dentro de sua marca pai.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-146">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="c9aa9-147">Normalmente, `<para>` é usado dentro de uma marcação, como `<remarks>` ou `<returns>`, para dividir o texto em parágrafos.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-147">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="c9aa9-148">Você pode formatar o conteúdo da marcação `<remarks>` para a definição de classe.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-148">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="c9aa9-149">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-149">&lt;c&gt;</span></span>

<span data-ttu-id="c9aa9-150">Ainda com relação à formatação, use a marca `<c>` para marcar parte do texto como código.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-150">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="c9aa9-151">Ela é semelhante à marca `<code>`, mas embutida.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-151">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="c9aa9-152">Ela é útil quando você deseja mostrar um exemplo de código rápido como parte do conteúdo da marca.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-152">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="c9aa9-153">Vamos atualizar a documentação para a classe `Math`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-153">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="c9aa9-154">&lt;exception&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-154">&lt;exception&gt;</span></span>

<span data-ttu-id="c9aa9-155">Usando a marca `<exception>`, você informa os desenvolvedores de que um método pode lançar exceções específicas.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-155">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="c9aa9-156">Observando sua biblioteca `Math`, você pode ver que ambos os métodos `Add` lançarão uma exceção se uma determinada condição for atendida.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-156">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="c9aa9-157">Algo menos óbvio, porém, é que o método inteiro `Divide` também será lançado se o parâmetro `b` for zero.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-157">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="c9aa9-158">Agora, adicione a documentação de exceção a esse método.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-158">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="c9aa9-159">O atributo `cref` representa uma referência a uma exceção que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-159">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="c9aa9-160">Pode ser qualquer tipo definido no projeto ou um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-160">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="c9aa9-161">O compilador emitirá um aviso se o valor não puder ser resolvido.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-161">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="c9aa9-162">&lt;see&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-162">&lt;see&gt;</span></span>

<span data-ttu-id="c9aa9-163">A marca `<see>` permite criar um link clicável para uma página de documentação para outro elemento de código.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-163">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="c9aa9-164">Em nosso próximo exemplo, criaremos um link clicável entre os dois métodos `Add`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-164">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="c9aa9-165">O `cref` é um atributo **obrigatório** que representa uma referência para um tipo ou seu membro que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-165">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="c9aa9-166">Pode ser qualquer tipo definido no projeto ou um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-166">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="c9aa9-167">&lt;seealso&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-167">&lt;seealso&gt;</span></span>

<span data-ttu-id="c9aa9-168">Você usa a marca `<seealso>` da mesma forma que usaria a marca `<see>`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-168">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="c9aa9-169">A única diferença é que seu conteúdo normalmente é colocado em uma seção "Consulte também".</span><span class="sxs-lookup"><span data-stu-id="c9aa9-169">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="c9aa9-170">Aqui, adicionaremos uma marca `seealso` ao método inteiro `Add` para fazer referência a outros métodos na classe que aceitam parâmetros inteiros:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-170">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="c9aa9-171">O atributo `cref` representa uma referência para um tipo ou seu membro que está disponível no ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-171">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="c9aa9-172">Pode ser qualquer tipo definido no projeto ou um assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-172">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="c9aa9-173">&lt;param&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-173">&lt;param&gt;</span></span>

<span data-ttu-id="c9aa9-174">Você usa a marca `<param>` para descrever os parâmetros de um método.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-174">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="c9aa9-175">Este é um exemplo do método `Add` duplo: o parâmetro que a marca descreve é especificado no atributo `name` **obrigatório**.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-175">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="c9aa9-176">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-176">&lt;typeparam&gt;</span></span>

<span data-ttu-id="c9aa9-177">Use a marca `<typeparam>` exatamente como a marca `<param>`, mas para declarações de método ou de tipo genérico para descrever um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-177">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="c9aa9-178">Adicione um método genérico rápido à sua classe `Math` para verificar se uma quantidade é maior que outra.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-178">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="c9aa9-179">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-179">&lt;paramref&gt;</span></span>

<span data-ttu-id="c9aa9-180">Às vezes, você pode estar descrevendo o que um método faz, no que poderia ser uma marcação `<summary>` e talvez queira fazer uma referência a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-180">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="c9aa9-181">A marcação `<paramref>` é excelente para exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-181">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="c9aa9-182">Vamos atualizar o resumo de nosso método `Add` de base dupla.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-182">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="c9aa9-183">Assim como a marca `<param>`, o nome do parâmetro é especificado no atributo `name` **obrigatório**.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-183">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="c9aa9-184">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-184">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="c9aa9-185">Use a marca `<typeparamref>` exatamente como a marca `<paramref>`, mas para declarações de método ou de tipo genérico para descrever um parâmetro genérico.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-185">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="c9aa9-186">É possível usar o mesmo método genérico criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-186">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="c9aa9-187">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-187">&lt;list&gt;</span></span>

<span data-ttu-id="c9aa9-188">Use a marca `<list>` para formatar informações de documentação como uma lista ordenada, uma lista não ordenada ou uma tabela.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-188">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="c9aa9-189">Crie uma lista não ordenada de cada operação matemática a que sua biblioteca `Math` dá suporte.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-189">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="c9aa9-190">É possível fazer uma lista ordenada ou tabela alterando o atributo `type` para `number` ou `table`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-190">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="c9aa9-191">Juntando as peças</span><span class="sxs-lookup"><span data-stu-id="c9aa9-191">Putting it all together</span></span>

<span data-ttu-id="c9aa9-192">Se você seguiu o tutorial e aplicou as marcas ao seu código quando necessário, seu código deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-192">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="c9aa9-193">No seu código, você pode gerar um site de documentação detalhada completo com referências cruzadas clicáveis.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-193">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="c9aa9-194">Mas você se depara com outro problema: o código tornou-se difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-194">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="c9aa9-195">Há tanta informação para ser analisada que será um pesadelo para qualquer desenvolvedor que desejar contribuir para esse código.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-195">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="c9aa9-196">Felizmente, há uma marca XML que pode ajudá-lo a lidar com isso:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-196">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="c9aa9-197">&lt;include&gt;</span><span class="sxs-lookup"><span data-stu-id="c9aa9-197">&lt;include&gt;</span></span>

<span data-ttu-id="c9aa9-198">A marcação `<include>` permite fazer referência a comentários em um arquivo XML separado que descrevem os tipos e membros em seu código-fonte, em vez de colocar comentários de documentação diretamente em seu arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-198">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="c9aa9-199">Agora, você moverá todas as suas marcas XML para um arquivo XML separado chamado `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-199">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="c9aa9-200">Fique à vontade para nomear o arquivo como desejar.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-200">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="c9aa9-201">No XML acima, os comentários de documentação de cada membro aparecem diretamente dentro de uma marca cujo nome corresponde ao que eles fazem.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-201">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="c9aa9-202">Você pode escolher sua própria estratégia.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-202">You can choose your own strategy.</span></span>
<span data-ttu-id="c9aa9-203">Agora que você tem seus comentários XML em um arquivo separado, vamos ver como seu código pode ficar mais legível usando a marca `<include>`:</span><span class="sxs-lookup"><span data-stu-id="c9aa9-203">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="c9aa9-204">E aqui está: nosso código voltou a ser legível e nenhuma informação de documentação foi perdida.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-204">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="c9aa9-205">O atributo `filename` representa o nome do arquivo XML que contém a documentação.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-205">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="c9aa9-206">O atributo `path` representa uma consulta [XPath](https://msdn.microsoft.com/library/ms256115.aspx) para o `tag name` presente no `filename` especificado.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-206">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="c9aa9-207">O atributo `name` representa o especificador de nome na marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-207">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="c9aa9-208">O atributo `id` que pode ser usado no lugar de `name` representa a ID da marca que precede os comentários.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-208">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="c9aa9-209">Marcas definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="c9aa9-209">User Defined Tags</span></span>

<span data-ttu-id="c9aa9-210">Todas as marcas descritas acima representam as marcas que são reconhecidas pelo compilador C#.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-210">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="c9aa9-211">No entanto, o usuário é livre para definir suas próprias marcas.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-211">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="c9aa9-212">Ferramentas como o Sandcastle dão suporte para marcas extras, como [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) e até mesmo à [documentação de namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="c9aa9-212">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="c9aa9-213">Ferramentas de geração de documentação internas ou personalizadas também podem ser usadas com as marcas padrão e vários formatos de saída, de HTML a PDF, podem ter suporte.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-213">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="c9aa9-214">Recomendações</span><span class="sxs-lookup"><span data-stu-id="c9aa9-214">Recommendations</span></span>

<span data-ttu-id="c9aa9-215">Documentar o código é recomendável por vários motivos.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-215">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="c9aa9-216">A seguir, temos algumas práticas recomendadas, cenários de caso de uso gerais e coisas que você precisa saber ao usar marcas de documentação XML em seu código C#.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-216">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="c9aa9-217">Para fins de consistência, todos os tipos visíveis publicamente e seus membros devem ser documentados.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-217">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="c9aa9-218">Se você precisar fazer isso, faça tudo.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-218">If you must do it, do it all.</span></span>
* <span data-ttu-id="c9aa9-219">Membros particulares também podem ser documentados usando comentários XML.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-219">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="c9aa9-220">No entanto, isso expõe o funcionamento interno (potencialmente confidencial) de sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-220">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="c9aa9-221">No mínimo, os tipos e seus membros devem ter uma marca `<summary>`, porque seu conteúdo é necessário para o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-221">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="c9aa9-222">O texto da documentação deve ser escrito usando frases terminadas com ponto final.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-222">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="c9aa9-223">Classes parciais têm suporte total e informações da documentação serão concatenadas em uma única entrada para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-223">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="c9aa9-224">O compilador verifica a sintaxe das marcas `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` e `<typeparam>`.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-224">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="c9aa9-225">O compilador valida os parâmetros que contêm caminhos de arquivo e referências para outras partes do código.</span><span class="sxs-lookup"><span data-stu-id="c9aa9-225">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9aa9-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9aa9-226">See also</span></span>

* [<span data-ttu-id="c9aa9-227">Comentários de documentação XML (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c9aa9-227">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)
* [<span data-ttu-id="c9aa9-228">Marcas recomendadas para comentários de documentação (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c9aa9-228">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
