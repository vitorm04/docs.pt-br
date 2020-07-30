---
title: Convenções de codificação em C# – Guia de Programação em C#
description: Saiba mais sobre convenções de codificação em C#. As convenções de codificação criam uma aparência consistente para o código e facilitam a cópia, a alteração e a manutenção do código.
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 772aebff0b8c7aebe7c7d5c7634cd2931f4570b1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301847"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="91b40-104">Convenções de codificação em C# (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="91b40-104">C# Coding Conventions (C# Programming Guide)</span></span>

<span data-ttu-id="91b40-105">As convenções de codificação atendem às seguintes finalidades:</span><span class="sxs-lookup"><span data-stu-id="91b40-105">Coding conventions serve the following purposes:</span></span>  
  
- <span data-ttu-id="91b40-106">Criam uma aparência consistente para o código, para que os leitores possam se concentrar no conteúdo e não no layout.</span><span class="sxs-lookup"><span data-stu-id="91b40-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
- <span data-ttu-id="91b40-107">Permitem que os leitores entendam o código com mais rapidez, fazendo suposições com base na experiência anterior.</span><span class="sxs-lookup"><span data-stu-id="91b40-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="91b40-108">Facilitam a cópia, a alteração e a manutenção do código.</span><span class="sxs-lookup"><span data-stu-id="91b40-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
- <span data-ttu-id="91b40-109">Demonstram as práticas recomendadas do C#.</span><span class="sxs-lookup"><span data-stu-id="91b40-109">They demonstrate C# best practices.</span></span>  

<span data-ttu-id="91b40-110">As diretrizes neste artigo são usadas pela Microsoft para desenvolver exemplos e documentação.</span><span class="sxs-lookup"><span data-stu-id="91b40-110">The guidelines in this article are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="91b40-111">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="91b40-111">Naming Conventions</span></span>  
  
- <span data-ttu-id="91b40-112">Em exemplos curtos que não incluem [diretivas using](../../language-reference/keywords/using-directive.md), use as qualificações do namespace.</span><span class="sxs-lookup"><span data-stu-id="91b40-112">In short examples that do not include [using directives](../../language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="91b40-113">Se você souber que um namespace é importado por padrão em um projeto, não precisará qualificar totalmente os nomes desse namespace.</span><span class="sxs-lookup"><span data-stu-id="91b40-113">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="91b40-114">Nomes qualificados podem ser interrompidos após um ponto (.) se forem muito longos para uma única linha, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-114">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
- <span data-ttu-id="91b40-115">Não é necessário alterar os nomes de objetos que foram criados usando as ferramentas de designer do Visual Studio para adequá-los a outras diretrizes.</span><span class="sxs-lookup"><span data-stu-id="91b40-115">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="91b40-116">Convenções de Layout</span><span class="sxs-lookup"><span data-stu-id="91b40-116">Layout Conventions</span></span>  

<span data-ttu-id="91b40-117">Um bom layout usa formatação para enfatizar a estrutura do código e para facilitar a leitura de código.</span><span class="sxs-lookup"><span data-stu-id="91b40-117">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="91b40-118">Exemplos e amostras Microsoft estão em conformidade com as seguintes convenções:</span><span class="sxs-lookup"><span data-stu-id="91b40-118">Microsoft examples and samples conform to the following conventions:</span></span>  
  
- <span data-ttu-id="91b40-119">Use as configurações padrão do Editor de códigos (recuo inteligente, recuos de quatro caracteres, guias salvas como espaços).</span><span class="sxs-lookup"><span data-stu-id="91b40-119">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="91b40-120">Para obter mais informações, consulte [Opções, Editor de Texto, C#, Formatação](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="91b40-120">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
- <span data-ttu-id="91b40-121">Gravar apenas uma instrução por linha.</span><span class="sxs-lookup"><span data-stu-id="91b40-121">Write only one statement per line.</span></span>  
  
- <span data-ttu-id="91b40-122">Gravar apenas uma declaração por linha.</span><span class="sxs-lookup"><span data-stu-id="91b40-122">Write only one declaration per line.</span></span>  
  
- <span data-ttu-id="91b40-123">Se as linhas de continuação não devem recuar automaticamente, recue-as uma tabulação (quatro espaços).</span><span class="sxs-lookup"><span data-stu-id="91b40-123">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
- <span data-ttu-id="91b40-124">Adicione pelo menos uma linha em branco entre as definições de método e de propriedade.</span><span class="sxs-lookup"><span data-stu-id="91b40-124">Add at least one blank line between method definitions and property definitions.</span></span>  
  
- <span data-ttu-id="91b40-125">Use parênteses para criar cláusulas em uma expressão aparente, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-125">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="91b40-126">Comentando Convenções</span><span class="sxs-lookup"><span data-stu-id="91b40-126">Commenting Conventions</span></span>  
  
- <span data-ttu-id="91b40-127">Coloque o comentário em uma linha separada, não no final de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="91b40-127">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
- <span data-ttu-id="91b40-128">Comece o texto do comentário com uma letra maiúscula.</span><span class="sxs-lookup"><span data-stu-id="91b40-128">Begin comment text with an uppercase letter.</span></span>  
  
- <span data-ttu-id="91b40-129">Termine o texto do comentário com um ponto final.</span><span class="sxs-lookup"><span data-stu-id="91b40-129">End comment text with a period.</span></span>  
  
- <span data-ttu-id="91b40-130">Insira um espaço entre o delimitador de comentário (/ /) e o texto do comentário, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-130">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
- <span data-ttu-id="91b40-131">Não crie blocos de asteriscos formatados em torno dos comentários.</span><span class="sxs-lookup"><span data-stu-id="91b40-131">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="91b40-132">Diretrizes de Linguagem</span><span class="sxs-lookup"><span data-stu-id="91b40-132">Language Guidelines</span></span>  

<span data-ttu-id="91b40-133">As seções a seguir descrevem práticas que a equipe de C# segue para preparar exemplos e amostras do código.</span><span class="sxs-lookup"><span data-stu-id="91b40-133">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="91b40-134">Tipo de dados da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="91b40-134">String Data Type</span></span>  
  
- <span data-ttu-id="91b40-135">Use a [interpolação de cadeia de caracteres](../../language-reference/tokens/interpolated.md) para concatenar cadeias de caracteres curtas, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-135">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
- <span data-ttu-id="91b40-136">Para acrescentar cadeias de caracteres em loops, especialmente quando você estiver trabalhando com grandes quantidades de texto, use um objeto <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="91b40-136">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="91b40-137">Variáveis Locais Tipadas Implicitamente</span><span class="sxs-lookup"><span data-stu-id="91b40-137">Implicitly Typed Local Variables</span></span>  
  
- <span data-ttu-id="91b40-138">Use a [digitação implícita](../classes-and-structs/implicitly-typed-local-variables.md) para variáveis locais quando o tipo da variável for óbvio do lado direito da atribuição ou quando o tipo exato não for importante.</span><span class="sxs-lookup"><span data-stu-id="91b40-138">Use [implicit typing](../classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
- <span data-ttu-id="91b40-139">Não use [var](../../language-reference/keywords/var.md) quando o tipo não estiver aparente no lado direito da atribuição.</span><span class="sxs-lookup"><span data-stu-id="91b40-139">Do not use [var](../../language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
- <span data-ttu-id="91b40-140">Não se baseie no nome da variável para especificar o tipo dela.</span><span class="sxs-lookup"><span data-stu-id="91b40-140">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="91b40-141">Ele pode não estar correto.</span><span class="sxs-lookup"><span data-stu-id="91b40-141">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
- <span data-ttu-id="91b40-142">Evite o uso de `var` em vez de [dynamic](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="91b40-142">Avoid the use of `var` in place of [dynamic](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="91b40-143">Use a digitação implícita para determinar o tipo da variável de loop nos loops [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="91b40-143">Use implicit typing to determine the type of the loop variable in [for](../../language-reference/keywords/for.md) loops.</span></span>  
  
     <span data-ttu-id="91b40-144">O exemplo a seguir usa digitação implícita em uma instrução `for`.</span><span class="sxs-lookup"><span data-stu-id="91b40-144">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  

- <span data-ttu-id="91b40-145">Não use a digitação implícita para determinar o tipo da variável de loop em loops [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="91b40-145">Do not use implicit typing to determine the type of the loop variable in [foreach](../../language-reference/keywords/foreach-in.md) loops.</span></span>

     <span data-ttu-id="91b40-146">O exemplo a seguir usa a digitação explícita em uma `foreach` instrução.</span><span class="sxs-lookup"><span data-stu-id="91b40-146">The following example uses explicit typing in a `foreach` statement.</span></span>

     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]

     > [!NOTE]
     > <span data-ttu-id="91b40-147">Tenha cuidado para não alterar acidentalmente um tipo de elemento da coleção iterável.</span><span class="sxs-lookup"><span data-stu-id="91b40-147">Be careful not to accidentally change a type of an element of the iterable collection.</span></span> <span data-ttu-id="91b40-148">Por exemplo, é fácil alternar de <xref:System.Linq.IQueryable?displayProperty=nameWithType> para <xref:System.Collections.IEnumerable?displayProperty=nameWithType> em uma `foreach` instrução, que altera a execução de uma consulta.</span><span class="sxs-lookup"><span data-stu-id="91b40-148">For example, it is easy to switch from <xref:System.Linq.IQueryable?displayProperty=nameWithType> to <xref:System.Collections.IEnumerable?displayProperty=nameWithType> in a `foreach` statement, which changes the execution of a query.</span></span>

### <a name="unsigned-data-type"></a><span data-ttu-id="91b40-149">Tipo de Dados Sem Sinal</span><span class="sxs-lookup"><span data-stu-id="91b40-149">Unsigned Data Type</span></span>  
  
<span data-ttu-id="91b40-150">Em geral, use `int` em vez de tipos sem assinatura.</span><span class="sxs-lookup"><span data-stu-id="91b40-150">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="91b40-151">O uso de `int` é comum em todo o C#, e é mais fácil interagir com outras bibliotecas ao usar `int`.</span><span class="sxs-lookup"><span data-stu-id="91b40-151">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="91b40-152">Matrizes</span><span class="sxs-lookup"><span data-stu-id="91b40-152">Arrays</span></span>  
  
<span data-ttu-id="91b40-153">Use a sintaxe concisa ao inicializar matrizes na linha da declaração.</span><span class="sxs-lookup"><span data-stu-id="91b40-153">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="91b40-154">Delegados</span><span class="sxs-lookup"><span data-stu-id="91b40-154">Delegates</span></span>  
  
<span data-ttu-id="91b40-155">Use a sintaxe concisa ao criar instâncias de um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="91b40-155">Use the concise syntax to create instances of a delegate type.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
[!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="91b40-156">try-catch e instruções de uso no tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="91b40-156">try-catch and using Statements in Exception Handling</span></span>  
  
- <span data-ttu-id="91b40-157">Use uma instrução [try-catch](../../language-reference/keywords/try-catch.md) para a maioria da manipulação de exceções.</span><span class="sxs-lookup"><span data-stu-id="91b40-157">Use a [try-catch](../../language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
- <span data-ttu-id="91b40-158">Simplifique o código usando a [instrução using](../../language-reference/keywords/using-statement.md) do #C.</span><span class="sxs-lookup"><span data-stu-id="91b40-158">Simplify your code by using the C# [using statement](../../language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="91b40-159">Se você tiver uma instrução [try-finally](../../language-reference/keywords/try-finally.md) na qual o único código do bloco `finally` é uma chamada para o método <xref:System.IDisposable.Dispose%2A>, use, em vez disso, uma instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="91b40-159">If you have a [try-finally](../../language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="91b40-160">Operadores && e &#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="91b40-160">&& and &#124;&#124; Operators</span></span>  
  
<span data-ttu-id="91b40-161">Para evitar exceções e aumentar o desempenho ignorando comparações desnecessárias, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) em vez de [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) e [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) em vez de [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) quando você executa comparações, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-161">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) instead of [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-) and [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) instead of [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-) when you perform comparisons, as shown in the following example.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="91b40-162">Operador New</span><span class="sxs-lookup"><span data-stu-id="91b40-162">New Operator</span></span>  
  
- <span data-ttu-id="91b40-163">Use um formulário conciso de instanciação de objeto com digitação implícita, conforme mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-163">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="91b40-164">A linha anterior é equivalente à declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="91b40-164">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
- <span data-ttu-id="91b40-165">Use inicializadores de objeto para simplificar a criação do objeto.</span><span class="sxs-lookup"><span data-stu-id="91b40-165">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="91b40-166">Tratamento de Evento</span><span class="sxs-lookup"><span data-stu-id="91b40-166">Event Handling</span></span>  
  
<span data-ttu-id="91b40-167">Se você estiver definindo um manipulador de eventos que não necessita ser removido posteriormente, use uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="91b40-167">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
[!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
[!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="91b40-168">Membros Estáticos</span><span class="sxs-lookup"><span data-stu-id="91b40-168">Static Members</span></span>  
  
<span data-ttu-id="91b40-169">Chame membros [estáticos](../../language-reference/keywords/static.md) usando o nome de classe: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="91b40-169">Call [static](../../language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="91b40-170">Essa prática torna o código mais legível, tornando o acesso estático limpo.</span><span class="sxs-lookup"><span data-stu-id="91b40-170">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="91b40-171">Não qualifique um membro estático definido em uma classe base com o nome de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="91b40-171">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="91b40-172">Enquanto esse código é compilado, a leitura do código fica incorreta e o código poderá ser danificado no futuro se você adicionar um membro estático com o mesmo nome da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="91b40-172">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="91b40-173">Consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="91b40-173">LINQ Queries</span></span>  
  
- <span data-ttu-id="91b40-174">Use nomes significativos para variáveis de consulta.</span><span class="sxs-lookup"><span data-stu-id="91b40-174">Use meaningful names for query variables.</span></span> <span data-ttu-id="91b40-175">O exemplo a seguir usa `seattleCustomers` para os clientes que estão localizados em Seattle.</span><span class="sxs-lookup"><span data-stu-id="91b40-175">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="91b40-176">Use aliases para se certificar de que os nomes de propriedades de tipos anônimos sejam colocados corretamente em maiúsculas, usando o padrão Pascal-Case.</span><span class="sxs-lookup"><span data-stu-id="91b40-176">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
- <span data-ttu-id="91b40-177">Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos.</span><span class="sxs-lookup"><span data-stu-id="91b40-177">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="91b40-178">Por exemplo, se a sua consulta retornar um nome de cliente e uma ID de distribuidor, em vez de deixá-los como `Name` e `ID` no resultado, renomeie-os para esclarecer que `Name` é o nome de um cliente, e `ID` é a identificação de um distribuidor.</span><span class="sxs-lookup"><span data-stu-id="91b40-178">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
- <span data-ttu-id="91b40-179">Usa a digitação implícita na declaração de variáveis de consulta e de intervalo.</span><span class="sxs-lookup"><span data-stu-id="91b40-179">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
- <span data-ttu-id="91b40-180">Alinhe cláusulas de consulta na cláusula [from](../../language-reference/keywords/from-clause.md), conforme mostrado nos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="91b40-180">Align query clauses under the [from](../../language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
- <span data-ttu-id="91b40-181">Use cláusulas [where](../../language-reference/keywords/where-clause.md) antes de outras cláusulas de consulta para garantir que cláusulas de consulta posteriores operem no conjunto de dados filtrado e reduzido.</span><span class="sxs-lookup"><span data-stu-id="91b40-181">Use [where](../../language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
- <span data-ttu-id="91b40-182">Use várias cláusulas `from` em vez de uma cláusula [join](../../language-reference/keywords/join-clause.md) para acessar coleções internas.</span><span class="sxs-lookup"><span data-stu-id="91b40-182">Use multiple `from` clauses instead of a [join](../../language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="91b40-183">Por exemplo, cada coleção de objetos `Student` pode conter um conjunto de pontuações no teste.</span><span class="sxs-lookup"><span data-stu-id="91b40-183">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="91b40-184">Quando a próxima consulta for executada, ela retorna cada pontuação que seja acima de 90, juntamente com o sobrenome do estudante que recebeu a pontuação.</span><span class="sxs-lookup"><span data-stu-id="91b40-184">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="91b40-185">Segurança</span><span class="sxs-lookup"><span data-stu-id="91b40-185">Security</span></span>  

<span data-ttu-id="91b40-186">Siga as diretrizes em [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="91b40-186">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b40-187">Veja também</span><span class="sxs-lookup"><span data-stu-id="91b40-187">See also</span></span>

- [<span data-ttu-id="91b40-188">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91b40-188">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)
- [<span data-ttu-id="91b40-189">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="91b40-189">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
