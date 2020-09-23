---
title: Estrutura de um programa Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 90bc1fd62a05f670424e1fac368376401d1030c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097768"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="abcd8-102">Estrutura de um programa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abcd8-102">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="abcd8-103">Um programa de Visual Basic é criado A partir dos blocos de construção padrão.</span><span class="sxs-lookup"><span data-stu-id="abcd8-103">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="abcd8-104">Uma *solução* consiste em um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="abcd8-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="abcd8-105">Um *projeto* , por sua vez, pode conter um ou mais assemblies.</span><span class="sxs-lookup"><span data-stu-id="abcd8-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="abcd8-106">Cada *assembly* é compilado de um ou mais arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="abcd8-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="abcd8-107">Um *arquivo de origem* fornece a definição e a implementação de classes, estruturas, módulos e interfaces, que, por fim, contêm todo o seu código.</span><span class="sxs-lookup"><span data-stu-id="abcd8-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="abcd8-108">Para obter mais informações sobre esses blocos de construção de um programa de Visual Basic, consulte [soluções e projetos](/visualstudio/ide/solutions-and-projects-in-visual-studio) e [assemblies no .net](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="abcd8-108">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="abcd8-109">Elementos de programação em nível de arquivo</span><span class="sxs-lookup"><span data-stu-id="abcd8-109">File-Level Programming Elements</span></span>  

 <span data-ttu-id="abcd8-110">Quando você inicia um projeto ou arquivo e abre o editor de código, você vê algum código já em vigor e na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="abcd8-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="abcd8-111">Qualquer código que você escrever deve seguir a seguinte sequência:</span><span class="sxs-lookup"><span data-stu-id="abcd8-111">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="abcd8-112">`Option` instruções</span><span class="sxs-lookup"><span data-stu-id="abcd8-112">`Option` statements</span></span>  
  
2. <span data-ttu-id="abcd8-113">`Imports` instruções</span><span class="sxs-lookup"><span data-stu-id="abcd8-113">`Imports` statements</span></span>  
  
3. <span data-ttu-id="abcd8-114">`Namespace` instruções e elementos de nível de namespace</span><span class="sxs-lookup"><span data-stu-id="abcd8-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="abcd8-115">Se você inserir instruções em uma ordem diferente, poderão ocorrer erros de compilação.</span><span class="sxs-lookup"><span data-stu-id="abcd8-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="abcd8-116">Um programa também pode conter instruções de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="abcd8-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="abcd8-117">Você pode intercalar esses arquivos no arquivo de origem entre as instruções da sequência anterior.</span><span class="sxs-lookup"><span data-stu-id="abcd8-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="abcd8-118">Instruções de opção</span><span class="sxs-lookup"><span data-stu-id="abcd8-118">Option Statements</span></span>  

 <span data-ttu-id="abcd8-119">`Option` as instruções estabelecem regras básicas para o código subsequente, ajudando a evitar erros de sintaxe e lógica.</span><span class="sxs-lookup"><span data-stu-id="abcd8-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="abcd8-120">A [instrução Option Explicit](../../language-reference/statements/option-explicit-statement.md) garante que todas as variáveis sejam declaradas e escritas corretamente, o que reduz o tempo de depuração.</span><span class="sxs-lookup"><span data-stu-id="abcd8-120">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="abcd8-121">A [instrução Option Strict](../../language-reference/statements/option-strict-statement.md) ajuda a minimizar erros lógicos e perda de dados que podem ocorrer quando você trabalha entre variáveis de tipos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="abcd8-121">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="abcd8-122">A [instrução Option Compare](../../language-reference/statements/option-compare-statement.md) especifica a maneira como as cadeias de caracteres são comparadas entre si, com base em seus `Binary` `Text` valores ou.</span><span class="sxs-lookup"><span data-stu-id="abcd8-122">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="abcd8-123">Instruções Imports</span><span class="sxs-lookup"><span data-stu-id="abcd8-123">Imports Statements</span></span>  

 <span data-ttu-id="abcd8-124">Você pode incluir uma [instrução Imports (namespace e tipo do .net)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) para importar nomes definidos fora do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="abcd8-124">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="abcd8-125">Uma `Imports` instrução permite que seu código faça referência a classes e a outros tipos definidos no namespace importado, sem precisar qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="abcd8-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="abcd8-126">Você pode usar tantas `Imports` instruções quantas forem apropriadas.</span><span class="sxs-lookup"><span data-stu-id="abcd8-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="abcd8-127">Para obter mais informações, consulte [References e a instrução Imports](references-and-the-imports-statement.md).</span><span class="sxs-lookup"><span data-stu-id="abcd8-127">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="abcd8-128">Instruções de namespace</span><span class="sxs-lookup"><span data-stu-id="abcd8-128">Namespace Statements</span></span>  

 <span data-ttu-id="abcd8-129">Os namespaces ajudam você a organizar e classificar seus elementos de programação para facilitar o agrupamento e o acesso.</span><span class="sxs-lookup"><span data-stu-id="abcd8-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="abcd8-130">Use a [instrução namespace](../../language-reference/statements/namespace-statement.md) para classificar as instruções a seguir em um namespace específico.</span><span class="sxs-lookup"><span data-stu-id="abcd8-130">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="abcd8-131">Para obter mais informações, consulte [Namespaces no Visual Basic](namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="abcd8-131">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="abcd8-132">Instruções de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="abcd8-132">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="abcd8-133">As instruções de compilação condicional podem aparecer quase em qualquer lugar no arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="abcd8-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="abcd8-134">Elas fazem com que partes do seu código sejam incluídas ou excluídas no tempo de compilação, dependendo de determinadas condições.</span><span class="sxs-lookup"><span data-stu-id="abcd8-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="abcd8-135">Você também pode usá-los para depurar seu aplicativo, pois o código condicional é executado somente no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="abcd8-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="abcd8-136">Para obter mais informações, consulte [compilação condicional](conditional-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="abcd8-136">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="abcd8-137">Elementos de programação de nível de namespace</span><span class="sxs-lookup"><span data-stu-id="abcd8-137">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="abcd8-138">Classes, estruturas e módulos contêm todo o código em seu arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="abcd8-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="abcd8-139">Eles são elementos *de nível de namespace* , que podem aparecer em um namespace ou no nível do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="abcd8-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="abcd8-140">Eles mantêm as declarações de todos os outros elementos de programação.</span><span class="sxs-lookup"><span data-stu-id="abcd8-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="abcd8-141">Interfaces, que definem as assinaturas de elemento, mas não fornecem nenhuma implementação, também aparecem no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="abcd8-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="abcd8-142">Para obter mais informações sobre os elementos de nível de módulo, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="abcd8-142">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="abcd8-143">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="abcd8-143">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="abcd8-144">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="abcd8-144">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="abcd8-145">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="abcd8-145">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="abcd8-146">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="abcd8-146">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="abcd8-147">Os elementos de dados no nível de namespace são enumerações e delegados.</span><span class="sxs-lookup"><span data-stu-id="abcd8-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="abcd8-148">Elementos de programação em nível de módulo</span><span class="sxs-lookup"><span data-stu-id="abcd8-148">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="abcd8-149">Procedimentos, operadores, propriedades e eventos são os únicos elementos de programação que podem conter código executável (instruções que executam ações em tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="abcd8-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="abcd8-150">Eles são os elementos de *nível de módulo* do seu programa.</span><span class="sxs-lookup"><span data-stu-id="abcd8-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="abcd8-151">Para obter mais informações sobre os elementos de nível de procedimento, consulte o seguinte:</span><span class="sxs-lookup"><span data-stu-id="abcd8-151">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="abcd8-152">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="abcd8-152">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="abcd8-153">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="abcd8-153">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="abcd8-154">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="abcd8-154">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="abcd8-155">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="abcd8-155">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="abcd8-156">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="abcd8-156">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="abcd8-157">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="abcd8-157">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="abcd8-158">Os elementos de dados no nível do módulo são variáveis, constantes, enumerações e delegados.</span><span class="sxs-lookup"><span data-stu-id="abcd8-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="abcd8-159">Elementos de programação de nível de procedimento</span><span class="sxs-lookup"><span data-stu-id="abcd8-159">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="abcd8-160">A maior parte do conteúdo dos elementos de *nível de procedimento* são instruções Executáveis, que constituem o código de tempo de execução do seu programa.</span><span class="sxs-lookup"><span data-stu-id="abcd8-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="abcd8-161">Todo o código executável deve estar em algum procedimento (,,,,,,, `Function` `Sub` `Operator` `Get` `Set` `AddHandler` `RemoveHandler` `RaiseEvent` ).</span><span class="sxs-lookup"><span data-stu-id="abcd8-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="abcd8-162">Para obter mais informações, consulte [Instruções](../language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="abcd8-162">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="abcd8-163">Os elementos de dados no nível de procedimento são limitados a variáveis locais e constantes.</span><span class="sxs-lookup"><span data-stu-id="abcd8-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="abcd8-164">O procedimento principal</span><span class="sxs-lookup"><span data-stu-id="abcd8-164">The Main Procedure</span></span>  

 <span data-ttu-id="abcd8-165">O `Main` procedimento é o primeiro código a ser executado quando seu aplicativo tiver sido carregado.</span><span class="sxs-lookup"><span data-stu-id="abcd8-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="abcd8-166">`Main` serve como o ponto de partida e o controle geral para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abcd8-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="abcd8-167">Há quatro variedades de `Main` :</span><span class="sxs-lookup"><span data-stu-id="abcd8-167">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="abcd8-168">A variedade mais comum desse procedimento é `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="abcd8-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="abcd8-169">Para obter mais informações, consulte o [procedimento principal em Visual Basic](main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="abcd8-169">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abcd8-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="abcd8-170">See also</span></span>

- [<span data-ttu-id="abcd8-171">Procedimento principal no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abcd8-171">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="abcd8-172">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abcd8-172">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="abcd8-173">Limitações do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="abcd8-173">Visual Basic Limitations</span></span>](limitations.md)
