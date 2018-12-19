---
title: Convenções de codificação em C# – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
ms.openlocfilehash: 598f0e75a96a43162d0c626d00320effb418c7fd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241425"
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="c07a8-102">Convenções de codificação em C# (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c07a8-102">C# Coding Conventions (C# Programming Guide)</span></span>
 <span data-ttu-id="c07a8-103">As convenções de codificação atendem às seguintes finalidades:</span><span class="sxs-lookup"><span data-stu-id="c07a8-103">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="c07a8-104">Criam uma aparência consistente para o código, para que os leitores possam se concentrar no conteúdo e não no layout.</span><span class="sxs-lookup"><span data-stu-id="c07a8-104">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="c07a8-105">Permitem que os leitores entendam o código com mais rapidez, fazendo suposições com base na experiência anterior.</span><span class="sxs-lookup"><span data-stu-id="c07a8-105">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="c07a8-106">Facilitam a cópia, a alteração e a manutenção do código.</span><span class="sxs-lookup"><span data-stu-id="c07a8-106">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="c07a8-107">Demonstram as práticas recomendadas do C#.</span><span class="sxs-lookup"><span data-stu-id="c07a8-107">They demonstrate C# best practices.</span></span>  

 <span data-ttu-id="c07a8-108">As diretrizes neste tópico são usadas pela Microsoft para desenvolver amostras e documentação.</span><span class="sxs-lookup"><span data-stu-id="c07a8-108">The guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="c07a8-109">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="c07a8-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="c07a8-110">Em exemplos curtos que não incluem [diretivas using](../../../csharp/language-reference/keywords/using-directive.md), use as qualificações do namespace.</span><span class="sxs-lookup"><span data-stu-id="c07a8-110">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="c07a8-111">Se você souber que um namespace é importado por padrão em um projeto, não precisará qualificar totalmente os nomes desse namespace.</span><span class="sxs-lookup"><span data-stu-id="c07a8-111">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="c07a8-112">Nomes qualificados podem ser interrompidos após um ponto (.) se forem muito longos para uma única linha, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-112">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="c07a8-113">Não é necessário alterar os nomes de objetos que foram criados usando as ferramentas de designer do Visual Studio para adequá-los a outras diretrizes.</span><span class="sxs-lookup"><span data-stu-id="c07a8-113">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="c07a8-114">Convenções de Layout</span><span class="sxs-lookup"><span data-stu-id="c07a8-114">Layout Conventions</span></span>  
 <span data-ttu-id="c07a8-115">Um bom layout usa formatação para enfatizar a estrutura do código e para facilitar a leitura de código.</span><span class="sxs-lookup"><span data-stu-id="c07a8-115">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="c07a8-116">Exemplos e amostras Microsoft estão em conformidade com as seguintes convenções:</span><span class="sxs-lookup"><span data-stu-id="c07a8-116">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="c07a8-117">Use as configurações padrão do Editor de códigos (recuo inteligente, recuos de quatro caracteres, guias salvas como espaços).</span><span class="sxs-lookup"><span data-stu-id="c07a8-117">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="c07a8-118">Para obter mais informações, consulte [Opções, Editor de Texto, C#, Formatação](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="c07a8-118">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="c07a8-119">Gravar apenas uma instrução por linha.</span><span class="sxs-lookup"><span data-stu-id="c07a8-119">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="c07a8-120">Gravar apenas uma declaração por linha.</span><span class="sxs-lookup"><span data-stu-id="c07a8-120">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="c07a8-121">Se as linhas de continuação não devem recuar automaticamente, recue-as uma tabulação (quatro espaços).</span><span class="sxs-lookup"><span data-stu-id="c07a8-121">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="c07a8-122">Adicione pelo menos uma linha em branco entre as definições de método e de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c07a8-122">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="c07a8-123">Use parênteses para criar cláusulas em uma expressão aparente, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-123">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="c07a8-124">Comentando Convenções</span><span class="sxs-lookup"><span data-stu-id="c07a8-124">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="c07a8-125">Coloque o comentário em uma linha separada, não no final de uma linha de código.</span><span class="sxs-lookup"><span data-stu-id="c07a8-125">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="c07a8-126">Comece o texto do comentário com uma letra maiúscula.</span><span class="sxs-lookup"><span data-stu-id="c07a8-126">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="c07a8-127">Termine o texto do comentário com um ponto final.</span><span class="sxs-lookup"><span data-stu-id="c07a8-127">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="c07a8-128">Insira um espaço entre o delimitador de comentário (/ /) e o texto do comentário, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-128">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="c07a8-129">Não crie blocos de asteriscos formatados em torno dos comentários.</span><span class="sxs-lookup"><span data-stu-id="c07a8-129">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="c07a8-130">Diretrizes de Linguagem</span><span class="sxs-lookup"><span data-stu-id="c07a8-130">Language Guidelines</span></span>  
 <span data-ttu-id="c07a8-131">As seções a seguir descrevem práticas que a equipe de C# segue para preparar exemplos e amostras do código.</span><span class="sxs-lookup"><span data-stu-id="c07a8-131">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="c07a8-132">Tipo de dados da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c07a8-132">String Data Type</span></span>  
  
-   <span data-ttu-id="c07a8-133">Use a [interpolação de cadeia de caracteres](../../language-reference/tokens/interpolated.md) para concatenar cadeias de caracteres curtas, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-133">Use [string interpolation](../../language-reference/tokens/interpolated.md) to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="c07a8-134">Para acrescentar cadeias de caracteres em loops, especialmente quando você estiver trabalhando com grandes quantidades de texto, use um objeto <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c07a8-134">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="c07a8-135">Variáveis Locais Tipadas Implicitamente</span><span class="sxs-lookup"><span data-stu-id="c07a8-135">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="c07a8-136">Use a [digitação implícita](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) para variáveis locais quando o tipo da variável for óbvio do lado direito da atribuição ou quando o tipo exato não for importante.</span><span class="sxs-lookup"><span data-stu-id="c07a8-136">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="c07a8-137">Não use [var](../../../csharp/language-reference/keywords/var.md) quando o tipo não estiver aparente no lado direito da atribuição.</span><span class="sxs-lookup"><span data-stu-id="c07a8-137">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="c07a8-138">Não se baseie no nome da variável para especificar o tipo dela.</span><span class="sxs-lookup"><span data-stu-id="c07a8-138">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="c07a8-139">Ele pode não estar correto.</span><span class="sxs-lookup"><span data-stu-id="c07a8-139">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="c07a8-140">Evite o uso de `var` em vez de [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="c07a8-140">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="c07a8-141">Use a digitação implícita para determinar o tipo da variável de loop nos loops [for](../../../csharp/language-reference/keywords/for.md) e [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="c07a8-141">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="c07a8-142">O exemplo a seguir usa digitação implícita em uma instrução `for`.</span><span class="sxs-lookup"><span data-stu-id="c07a8-142">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="c07a8-143">O exemplo a seguir usa digitação implícita em uma instrução `foreach`.</span><span class="sxs-lookup"><span data-stu-id="c07a8-143">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="c07a8-144">Tipo de Dados Sem Sinal</span><span class="sxs-lookup"><span data-stu-id="c07a8-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="c07a8-145">Em geral, use `int` em vez de tipos sem assinatura.</span><span class="sxs-lookup"><span data-stu-id="c07a8-145">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="c07a8-146">O uso de `int` é comum em todo o C#, e é mais fácil interagir com outras bibliotecas ao usar `int`.</span><span class="sxs-lookup"><span data-stu-id="c07a8-146">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="c07a8-147">Matrizes</span><span class="sxs-lookup"><span data-stu-id="c07a8-147">Arrays</span></span>  
  
-   <span data-ttu-id="c07a8-148">Use a sintaxe concisa ao inicializar matrizes na linha da declaração.</span><span class="sxs-lookup"><span data-stu-id="c07a8-148">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="c07a8-149">Delegados</span><span class="sxs-lookup"><span data-stu-id="c07a8-149">Delegates</span></span>  
  
-   <span data-ttu-id="c07a8-150">Use a sintaxe concisa ao criar instâncias de um tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="c07a8-150">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="c07a8-151">try-catch e instruções de uso no tratamento de exceção</span><span class="sxs-lookup"><span data-stu-id="c07a8-151">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="c07a8-152">Use uma instrução [try-catch](../../../csharp/language-reference/keywords/try-catch.md) para a maioria da manipulação de exceções.</span><span class="sxs-lookup"><span data-stu-id="c07a8-152">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="c07a8-153">Simplifique o código usando a [instrução using](../../../csharp/language-reference/keywords/using-statement.md) do #C.</span><span class="sxs-lookup"><span data-stu-id="c07a8-153">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="c07a8-154">Se você tiver uma instrução [try-finally](../../../csharp/language-reference/keywords/try-finally.md) na qual o único código do bloco `finally` é uma chamada para o método <xref:System.IDisposable.Dispose%2A>, use, em vez disso, uma instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="c07a8-154">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="c07a8-155">Operadores && e &#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="c07a8-155">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="c07a8-156">Para evitar exceções e aumentar o desempenho ignorando comparações desnecessárias, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) em vez de [&](../../../csharp/language-reference/operators/and-operator.md) e [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) em vez de [&#124;](../../../csharp/language-reference/operators/or-operator.md) ao executar comparações, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-156">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="c07a8-157">Operador New</span><span class="sxs-lookup"><span data-stu-id="c07a8-157">New Operator</span></span>  
  
-   <span data-ttu-id="c07a8-158">Use um formulário conciso de instanciação de objeto com digitação implícita, conforme mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-158">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="c07a8-159">A linha anterior é equivalente à declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="c07a8-159">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="c07a8-160">Use inicializadores de objeto para simplificar a criação do objeto.</span><span class="sxs-lookup"><span data-stu-id="c07a8-160">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="c07a8-161">Tratamento de Evento</span><span class="sxs-lookup"><span data-stu-id="c07a8-161">Event Handling</span></span>  
  
-   <span data-ttu-id="c07a8-162">Se você estiver definindo um manipulador de eventos que não necessita ser removido posteriormente, use uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c07a8-162">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="c07a8-163">Membros Estáticos</span><span class="sxs-lookup"><span data-stu-id="c07a8-163">Static Members</span></span>  
  
-   <span data-ttu-id="c07a8-164">Chame membros [estáticos](../../../csharp/language-reference/keywords/static.md) usando o nome de classe: *ClassName.StaticMember*.</span><span class="sxs-lookup"><span data-stu-id="c07a8-164">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="c07a8-165">Essa prática torna o código mais legível, tornando o acesso estático limpo.</span><span class="sxs-lookup"><span data-stu-id="c07a8-165">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="c07a8-166">Não qualifique um membro estático definido em uma classe base com o nome de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c07a8-166">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="c07a8-167">Enquanto esse código é compilado, a leitura do código fica incorreta e o código poderá ser danificado no futuro se você adicionar um membro estático com o mesmo nome da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c07a8-167">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="c07a8-168">Consultas LINQ</span><span class="sxs-lookup"><span data-stu-id="c07a8-168">LINQ Queries</span></span>  
  
-   <span data-ttu-id="c07a8-169">Use nomes significativos para variáveis de consulta.</span><span class="sxs-lookup"><span data-stu-id="c07a8-169">Use meaningful names for query variables.</span></span> <span data-ttu-id="c07a8-170">O exemplo a seguir usa `seattleCustomers` para os clientes que estão localizados em Seattle.</span><span class="sxs-lookup"><span data-stu-id="c07a8-170">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="c07a8-171">Use aliases para se certificar de que os nomes de propriedades de tipos anônimos sejam colocados corretamente em maiúsculas, usando o padrão Pascal-Case.</span><span class="sxs-lookup"><span data-stu-id="c07a8-171">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="c07a8-172">Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos.</span><span class="sxs-lookup"><span data-stu-id="c07a8-172">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="c07a8-173">Por exemplo, se a sua consulta retornar um nome de cliente e uma ID de distribuidor, em vez de deixá-los como `Name` e `ID` no resultado, renomeie-os para esclarecer que `Name` é o nome de um cliente, e `ID` é a identificação de um distribuidor.</span><span class="sxs-lookup"><span data-stu-id="c07a8-173">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="c07a8-174">Usa a digitação implícita na declaração de variáveis de consulta e de intervalo.</span><span class="sxs-lookup"><span data-stu-id="c07a8-174">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="c07a8-175">Alinhe cláusulas de consulta na cláusula [from](../../../csharp/language-reference/keywords/from-clause.md), conforme mostrado nos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="c07a8-175">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="c07a8-176">Use cláusulas [where](../../../csharp/language-reference/keywords/where-clause.md) antes de outras cláusulas de consulta para garantir que cláusulas de consulta posteriores operem no conjunto de dados filtrado e reduzido.</span><span class="sxs-lookup"><span data-stu-id="c07a8-176">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="c07a8-177">Use várias cláusulas `from` em vez de uma cláusula [join](../../../csharp/language-reference/keywords/join-clause.md) para acessar coleções internas.</span><span class="sxs-lookup"><span data-stu-id="c07a8-177">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="c07a8-178">Por exemplo, cada coleção de objetos `Student` pode conter um conjunto de pontuações no teste.</span><span class="sxs-lookup"><span data-stu-id="c07a8-178">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="c07a8-179">Quando a próxima consulta for executada, ela retorna cada pontuação que seja acima de 90, juntamente com o sobrenome do estudante que recebeu a pontuação.</span><span class="sxs-lookup"><span data-stu-id="c07a8-179">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="c07a8-180">Segurança</span><span class="sxs-lookup"><span data-stu-id="c07a8-180">Security</span></span>  
 <span data-ttu-id="c07a8-181">Siga as diretrizes em [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="c07a8-181">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07a8-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c07a8-182">See Also</span></span>

- [<span data-ttu-id="c07a8-183">Convenções de codificação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c07a8-183">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
- [<span data-ttu-id="c07a8-184">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="c07a8-184">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
