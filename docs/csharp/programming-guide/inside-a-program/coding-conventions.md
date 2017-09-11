---
title: "Convenções de codificação em C# (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f32fdc0eb1954cdac30c39e05c74d43301d850c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="47d6a-102">Convenções de codificação em C# (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="47d6a-102">C# Coding Conventions (C# Programming Guide)</span></span>
<span data-ttu-id="47d6a-103">A [Especificação da Linguagem C#](http://go.microsoft.com/fwlink/?LinkId=199552) não define um padrão de codificação.</span><span class="sxs-lookup"><span data-stu-id="47d6a-103">The [C# Language Specification](http://go.microsoft.com/fwlink/?LinkId=199552) does not define a coding standard.</span></span> <span data-ttu-id="47d6a-104">No entanto, as diretrizes neste tópico são usadas pela Microsoft para desenvolver amostras e documentação.</span><span class="sxs-lookup"><span data-stu-id="47d6a-104">However, the guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
 <span data-ttu-id="47d6a-105">As convenções de codificação atendem às seguintes finalidades:</span><span class="sxs-lookup"><span data-stu-id="47d6a-105">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="47d6a-106">Criam uma aparência consistente para o código, para que os leitores possam se concentrar no conteúdo e não no layout.</span><span class="sxs-lookup"><span data-stu-id="47d6a-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="47d6a-107">Permitem que os leitores entendam o código com mais rapidez, fazendo suposições com base na experiência anterior.</span><span class="sxs-lookup"><span data-stu-id="47d6a-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="47d6a-108">Facilitam a cópia, a alteração e a manutenção do código.</span><span class="sxs-lookup"><span data-stu-id="47d6a-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="47d6a-109">Demonstram as práticas recomendadas do C#.</span><span class="sxs-lookup"><span data-stu-id="47d6a-109">They demonstrate C# best practices.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="47d6a-110">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="47d6a-110">Naming Conventions</span></span>  
  
-   <span data-ttu-id="47d6a-111">Em exemplos curtos que não incluem [diretivas using](../../../csharp/language-reference/keywords/using-directive.md), use as qualificações do namespace.</span><span class="sxs-lookup"><span data-stu-id="47d6a-111">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="47d6a-112">Se você souber que um namespace é importado por padrão em um projeto, não precisará qualificar totalmente os nomes desse namespace.</span><span class="sxs-lookup"><span data-stu-id="47d6a-112">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="47d6a-113">Nomes qualificados podem ser interrompidos após um ponto (.) se forem muito longos para uma única linha, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-113">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     <span data-ttu-id="47d6a-114">[!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-114">[!code-cs[csProgGuideCodingConventions#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_1.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-115">Não é necessário alterar os nomes de objetos que foram criados usando as ferramentas de designer do Visual Studio para adequá-los a outras diretrizes.</span><span class="sxs-lookup"><span data-stu-id="47d6a-115">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="47d6a-116">Convenções de Layout</span><span class="sxs-lookup"><span data-stu-id="47d6a-116">Layout Conventions</span></span>  
 <span data-ttu-id="47d6a-117">Um bom layout usa formatação para enfatizar a estrutura do código e para facilitar a leitura de código.</span><span class="sxs-lookup"><span data-stu-id="47d6a-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="47d6a-118">Exemplos e amostras Microsoft estão em conformidade com as seguintes convenções:</span><span class="sxs-lookup"><span data-stu-id="47d6a-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="47d6a-119">Use as configurações padrão do Editor de códigos (recuo inteligente, recuos de quatro caracteres, guias salvas como espaços).</span><span class="sxs-lookup"><span data-stu-id="47d6a-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="47d6a-120">Para obter mais informações, consulte [Opções, Editor de Texto, C#, Formatação](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="47d6a-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="47d6a-121">Gravar apenas uma instrução por linha.</span><span class="sxs-lookup"><span data-stu-id="47d6a-121">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="47d6a-122">Gravar apenas uma declaração por linha.</span><span class="sxs-lookup"><span data-stu-id="47d6a-122">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="47d6a-123">Se as linhas de continuação não devem recuar automaticamente, recue-as uma tabulação (quatro espaços).</span><span class="sxs-lookup"><span data-stu-id="47d6a-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="47d6a-124">Adicione pelo menos uma linha em branco entre as definições de método e de propriedade.</span><span class="sxs-lookup"><span data-stu-id="47d6a-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="47d6a-125">Use parênteses para criar cláusulas em uma expressão aparente, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     <span data-ttu-id="47d6a-126">[!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-126">[!code-cs[csProgGuideCodingConventions#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_2.cs)]</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="47d6a-127">Comentando Convenções</span><span class="sxs-lookup"><span data-stu-id="47d6a-127">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="47d6a-128">Coloque o comentário em uma linha separada, não no final de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="47d6a-128">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="47d6a-129">Comece o texto do comentário com uma letra maiúscula.</span><span class="sxs-lookup"><span data-stu-id="47d6a-129">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="47d6a-130">Termine o texto do comentário com um ponto final.</span><span class="sxs-lookup"><span data-stu-id="47d6a-130">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="47d6a-131">Insira um espaço entre o delimitador de comentário (/ /) e o texto do comentário, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-131">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     <span data-ttu-id="47d6a-132">[!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-132">[!code-cs[csProgGuideCodingConventions#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_3.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-133">Não crie blocos de asteriscos formatados em torno dos comentários.</span><span class="sxs-lookup"><span data-stu-id="47d6a-133">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="47d6a-134">Diretrizes de Linguagem</span><span class="sxs-lookup"><span data-stu-id="47d6a-134">Language Guidelines</span></span>  
 <span data-ttu-id="47d6a-135">As seções a seguir descrevem práticas que a equipe de C# segue para preparar exemplos e amostras do código.</span><span class="sxs-lookup"><span data-stu-id="47d6a-135">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="47d6a-136">Tipo de dados da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="47d6a-136">String Data Type</span></span>  
  
-   <span data-ttu-id="47d6a-137">Use o operador `+` para concatenar cadeias de caracteres curtas, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-137">Use the `+` operator to concatenate short strings, as shown in the following code.</span></span>  
  
     <span data-ttu-id="47d6a-138">[!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-138">[!code-cs[csProgGuideCodingConventions#6](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_4.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-139">Para acrescentar cadeias de caracteres em loops, especialmente quando você estiver trabalhando com grandes quantidades de texto, use um objeto <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="47d6a-139">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     <span data-ttu-id="47d6a-140">[!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-140">[!code-cs[csProgGuideCodingConventions#7](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_5.cs)]</span></span>  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="47d6a-141">Variáveis Locais Tipadas Implicitamente</span><span class="sxs-lookup"><span data-stu-id="47d6a-141">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="47d6a-142">Use a [digitação implícita](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) para variáveis locais quando o tipo da variável for óbvio do lado direito da atribuição ou quando o tipo exato não for importante.</span><span class="sxs-lookup"><span data-stu-id="47d6a-142">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     <span data-ttu-id="47d6a-143">[!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-143">[!code-cs[csProgGuideCodingConventions#8](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_6.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-144">Não use [var](../../../csharp/language-reference/keywords/var.md) quando o tipo não estiver aparente no lado direito da atribuição.</span><span class="sxs-lookup"><span data-stu-id="47d6a-144">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     <span data-ttu-id="47d6a-145">[!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-145">[!code-cs[csProgGuideCodingConventions#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_7.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-146">Não se baseie no nome da variável para especificar o tipo dela.</span><span class="sxs-lookup"><span data-stu-id="47d6a-146">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="47d6a-147">Ele pode não estar correto.</span><span class="sxs-lookup"><span data-stu-id="47d6a-147">It might not be correct.</span></span>  
  
     <span data-ttu-id="47d6a-148">[!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-148">[!code-cs[csProgGuideCodingConventions#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_8.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-149">Evite o uso de `var` em vez de [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="47d6a-149">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="47d6a-150">Use a digitação implícita para determinar o tipo da variável de loop nos loops [for](../../../csharp/language-reference/keywords/for.md) e [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="47d6a-150">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="47d6a-151">O exemplo a seguir usa digitação implícita em uma instrução `for`.</span><span class="sxs-lookup"><span data-stu-id="47d6a-151">The following example uses implicit typing in a `for` statement.</span></span>  
  
     <span data-ttu-id="47d6a-152">[!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-152">[!code-cs[csProgGuideCodingConventions#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_9.cs)]</span></span>  
  
     <span data-ttu-id="47d6a-153">O exemplo a seguir usa digitação implícita em uma instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="47d6a-153">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     <span data-ttu-id="47d6a-154">[!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-154">[!code-cs[csProgGuideCodingConventions#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_10.cs)]</span></span>  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="47d6a-155">Tipo de Dados Sem Sinal</span><span class="sxs-lookup"><span data-stu-id="47d6a-155">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="47d6a-156">Em geral, use `int` em vez de tipos sem assinatura.</span><span class="sxs-lookup"><span data-stu-id="47d6a-156">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="47d6a-157">O uso de `int` é comum em todo o C#, e é mais fácil interagir com outras bibliotecas ao usar `int`.</span><span class="sxs-lookup"><span data-stu-id="47d6a-157">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="47d6a-158">Matrizes</span><span class="sxs-lookup"><span data-stu-id="47d6a-158">Arrays</span></span>  
  
-   <span data-ttu-id="47d6a-159">Use a sintaxe concisa ao inicializar matrizes na linha da declaração.</span><span class="sxs-lookup"><span data-stu-id="47d6a-159">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     <span data-ttu-id="47d6a-160">[!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-160">[!code-cs[csProgGuideCodingConventions#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_11.cs)]</span></span>  
  
### <a name="delegates"></a><span data-ttu-id="47d6a-161">Delegados</span><span class="sxs-lookup"><span data-stu-id="47d6a-161">Delegates</span></span>  
  
-   <span data-ttu-id="47d6a-162">Use a sintaxe concisa ao criar instâncias de um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="47d6a-162">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     <span data-ttu-id="47d6a-163">[!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-163">[!code-cs[csProgGuideCodingConventions#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_12.cs)]</span></span>  
  
     <span data-ttu-id="47d6a-164">[!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-164">[!code-cs[csProgGuideCodingConventions#15](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_13.cs)]</span></span>  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="47d6a-165">try-catch e instruções de uso no tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="47d6a-165">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="47d6a-166">Use uma instrução [try-catch](../../../csharp/language-reference/keywords/try-catch.md) para a maioria da manipulação de exceções.</span><span class="sxs-lookup"><span data-stu-id="47d6a-166">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     <span data-ttu-id="47d6a-167">[!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-167">[!code-cs[csProgGuideCodingConventions#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_14.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-168">Simplifique o código usando a [instrução using](../../../csharp/language-reference/keywords/using-statement.md) do #C.</span><span class="sxs-lookup"><span data-stu-id="47d6a-168">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="47d6a-169">Se você tiver uma instrução [try-finally](../../../csharp/language-reference/keywords/try-finally.md) na qual o único código do bloco `finally` é uma chamada para o método <xref:System.IDisposable.Dispose%2A>, use, em vez disso, uma instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="47d6a-169">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     <span data-ttu-id="47d6a-170">[!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-170">[!code-cs[csProgGuideCodingConventions#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_15.cs)]</span></span>  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="47d6a-171">Operadores && e &#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="47d6a-171">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="47d6a-172">Para evitar exceções e aumentar o desempenho ignorando comparações desnecessárias, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) em vez de [&](../../../csharp/language-reference/operators/and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) em vez de [&#124;](../../../csharp/language-reference/operators/or-operator.md) ao executar comparações, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-172">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     <span data-ttu-id="47d6a-173">[!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-173">[!code-cs[csProgGuideCodingConventions#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_16.cs)]</span></span>  
  
### <a name="new-operator"></a><span data-ttu-id="47d6a-174">Operador New</span><span class="sxs-lookup"><span data-stu-id="47d6a-174">New Operator</span></span>  
  
-   <span data-ttu-id="47d6a-175">Use um formulário conciso de instanciação de objeto com digitação implícita, conforme mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-175">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     <span data-ttu-id="47d6a-176">[!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-176">[!code-cs[csProgGuideCodingConventions#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_17.cs)]</span></span>  
  
     <span data-ttu-id="47d6a-177">A linha anterior é equivalente à declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="47d6a-177">The previous line is equivalent to the following declaration.</span></span>  
  
     <span data-ttu-id="47d6a-178">[!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-178">[!code-cs[csProgGuideCodingConventions#20](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_18.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-179">Use inicializadores de objeto para simplificar a criação do objeto.</span><span class="sxs-lookup"><span data-stu-id="47d6a-179">Use object initializers to simplify object creation.</span></span>  
  
     <span data-ttu-id="47d6a-180">[!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-180">[!code-cs[csProgGuideCodingConventions#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_19.cs)]</span></span>  
  
### <a name="event-handling"></a><span data-ttu-id="47d6a-181">Tratamento de Evento</span><span class="sxs-lookup"><span data-stu-id="47d6a-181">Event Handling</span></span>  
  
-   <span data-ttu-id="47d6a-182">Se você estiver definindo um manipulador de eventos que não necessita ser removido posteriormente, use uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="47d6a-182">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     <span data-ttu-id="47d6a-183">[!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-183">[!code-cs[csProgGuideCodingConventions#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_20.cs)]</span></span>  
  
     <span data-ttu-id="47d6a-184">[!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-184">[!code-cs[csProgGuideCodingConventions#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_21.cs)]</span></span>  
  
### <a name="static-members"></a><span data-ttu-id="47d6a-185">Membros Estáticos</span><span class="sxs-lookup"><span data-stu-id="47d6a-185">Static Members</span></span>  
  
-   <span data-ttu-id="47d6a-186">Chame membros [estáticos](../../../csharp/language-reference/keywords/static.md) usando o nome de classe: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="47d6a-186">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="47d6a-187">Essa prática torna o código mais legível, tornando o acesso estático limpo.</span><span class="sxs-lookup"><span data-stu-id="47d6a-187">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="47d6a-188">Não qualifique um membro estático definido em uma classe base com o nome de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="47d6a-188">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="47d6a-189">Enquanto esse código é compilado, a leitura do código fica incorreta e o código poderá ser danificado no futuro se você adicionar um membro estático com o mesmo nome da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="47d6a-189">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="47d6a-190">Consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="47d6a-190">LINQ Queries</span></span>  
  
-   <span data-ttu-id="47d6a-191">Use nomes significativos para variáveis de consulta.</span><span class="sxs-lookup"><span data-stu-id="47d6a-191">Use meaningful names for query variables.</span></span> <span data-ttu-id="47d6a-192">O exemplo a seguir usa `seattleCustomers` para os clientes que estão localizados em Seattle.</span><span class="sxs-lookup"><span data-stu-id="47d6a-192">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     <span data-ttu-id="47d6a-193">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-193">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-194">Use aliases para se certificar de que os nomes de propriedades de tipos anônimos sejam colocados corretamente em maiúsculas, usando o padrão Pascal-Case.</span><span class="sxs-lookup"><span data-stu-id="47d6a-194">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     <span data-ttu-id="47d6a-195">[!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-195">[!code-cs[csProgGuideCodingConventions#26](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_23.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-196">Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos.</span><span class="sxs-lookup"><span data-stu-id="47d6a-196">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="47d6a-197">Por exemplo, se a sua consulta retornar um nome de cliente e uma ID de distribuidor, em vez de deixá-los como `Name` e `ID` no resultado, renomeie-os para esclarecer que `Name` é o nome de um cliente, e `ID` é a identificação de um distribuidor.</span><span class="sxs-lookup"><span data-stu-id="47d6a-197">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     <span data-ttu-id="47d6a-198">[!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-198">[!code-cs[csProgGuideCodingConventions#27](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_24.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-199">Usa a digitação implícita na declaração de variáveis de consulta e de intervalo.</span><span class="sxs-lookup"><span data-stu-id="47d6a-199">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     <span data-ttu-id="47d6a-200">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-200">[!code-cs[csProgGuideCodingConventions#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_22.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-201">Alinhe cláusulas de consulta na cláusula [from](../../../csharp/language-reference/keywords/from-clause.md), conforme mostrado nos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="47d6a-201">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="47d6a-202">Use cláusulas [where](../../../csharp/language-reference/keywords/where-clause.md) antes de outras cláusulas de consulta para garantir que cláusulas de consulta posteriores operem no conjunto de dados filtrado e reduzido.</span><span class="sxs-lookup"><span data-stu-id="47d6a-202">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     <span data-ttu-id="47d6a-203">[!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-203">[!code-cs[csProgGuideCodingConventions#29](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_25.cs)]</span></span>  
  
-   <span data-ttu-id="47d6a-204">Use várias cláusulas `from` em vez de uma cláusula [join](../../../csharp/language-reference/keywords/join-clause.md) para acessar coleções internas.</span><span class="sxs-lookup"><span data-stu-id="47d6a-204">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="47d6a-205">Por exemplo, cada coleção de objetos `Student` pode conter um conjunto de pontuações no teste.</span><span class="sxs-lookup"><span data-stu-id="47d6a-205">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="47d6a-206">Quando a próxima consulta for executada, ela retorna cada pontuação que seja acima de 90, juntamente com o sobrenome do estudante que recebeu a pontuação.</span><span class="sxs-lookup"><span data-stu-id="47d6a-206">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     <span data-ttu-id="47d6a-207">[!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]</span><span class="sxs-lookup"><span data-stu-id="47d6a-207">[!code-cs[csProgGuideCodingConventions#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/coding-conventions_26.cs)]</span></span>  
  
## <a name="security"></a><span data-ttu-id="47d6a-208">Segurança</span><span class="sxs-lookup"><span data-stu-id="47d6a-208">Security</span></span>  
 <span data-ttu-id="47d6a-209">Siga as diretrizes em [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="47d6a-209">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d6a-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47d6a-210">See Also</span></span>  
 <span data-ttu-id="47d6a-211">[Convenções de codificação do Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="47d6a-211">[Visual Basic Coding Conventions](../../../visual-basic/programming-guide/program-structure/coding-conventions.md) </span></span>  
 [<span data-ttu-id="47d6a-212">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="47d6a-212">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)

