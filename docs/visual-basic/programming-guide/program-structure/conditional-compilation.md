---
title: Compilação condicional no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 496df36242c6b43e7e3ec94ce675d11177e8b466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="49299-102">Compilação condicional no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="49299-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="49299-103">Em *compilação condicional*, determinados blocos de código em um programa são compilados seletivamente, enquanto outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49299-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="49299-104">Por exemplo, você talvez queira escrever declarações de depuração que comparam a velocidade das abordagens diferentes para a mesma tarefa de programação, ou você talvez queira localizar um aplicativo para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="49299-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="49299-105">Instruções de compilação condicional são projetadas para execução durante o tempo de compilação, não em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="49299-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="49299-106">Denota blocos de código para serem condicionalmente compilados com o `#If...Then...#Else` diretiva.</span><span class="sxs-lookup"><span data-stu-id="49299-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="49299-107">Por exemplo, para criar o francês e alemão versões do mesmo aplicativo o mesmo código-fonte, você deve inserir segmentos de código específico da plataforma em `#If...Then` instruções que usam constantes predefinidas `FrenchVersion` e `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="49299-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="49299-108">O exemplo a seguir demonstra como:</span><span class="sxs-lookup"><span data-stu-id="49299-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="49299-109">Se você definir o valor de `FrenchVersion` constante de compilação condicional para `True` em tempo de compilação, o código condicional para a versão francesa é compilado.</span><span class="sxs-lookup"><span data-stu-id="49299-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="49299-110">Se você definir o valor de `GermanVersion` constante para `True`, o compilador usa a versão em alemão.</span><span class="sxs-lookup"><span data-stu-id="49299-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="49299-111">Se não for definido como `True`, o código no último `Else` bloco é executado.</span><span class="sxs-lookup"><span data-stu-id="49299-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49299-112">Preenchimento automático será não funcionará quando a edição de código e usando diretivas de compilação condicional se o código não for parte da ramificação atual.</span><span class="sxs-lookup"><span data-stu-id="49299-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="49299-113">Declarando constantes de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="49299-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="49299-114">Você pode definir constantes de compilação condicional de uma das três maneiras:</span><span class="sxs-lookup"><span data-stu-id="49299-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="49299-115">No **Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="49299-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="49299-116">Na linha de comando ao usar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="49299-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="49299-117">Em seu código</span><span class="sxs-lookup"><span data-stu-id="49299-117">In your code</span></span>  
  
 <span data-ttu-id="49299-118">Constantes de compilação condicional tem um escopo especial e não podem ser acessados de código padrão.</span><span class="sxs-lookup"><span data-stu-id="49299-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="49299-119">O escopo de uma constante de compilação condicional é dependente da maneira que ele está definido.</span><span class="sxs-lookup"><span data-stu-id="49299-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="49299-120">A tabela a seguir lista o escopo das constantes declaradas usando cada uma das três maneiras mencionadas acima.</span><span class="sxs-lookup"><span data-stu-id="49299-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="49299-121">Configuração de constante</span><span class="sxs-lookup"><span data-stu-id="49299-121">How constant is set</span></span>|<span data-ttu-id="49299-122">Escopo de constante</span><span class="sxs-lookup"><span data-stu-id="49299-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="49299-123">**Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="49299-123">**Project Designer**</span></span>|<span data-ttu-id="49299-124">Público para todos os arquivos no projeto</span><span class="sxs-lookup"><span data-stu-id="49299-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="49299-125">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="49299-125">Command line</span></span>|<span data-ttu-id="49299-126">Público para todos os arquivos passadas para o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="49299-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="49299-127">`#Const` instrução em código</span><span class="sxs-lookup"><span data-stu-id="49299-127">`#Const` statement in code</span></span>|<span data-ttu-id="49299-128">Para o arquivo no qual ela é declarada privada</span><span class="sxs-lookup"><span data-stu-id="49299-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="49299-129">Para definir constantes no Designer de projeto</span><span class="sxs-lookup"><span data-stu-id="49299-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="49299-130">-A antes de criar o arquivo executável, definir constantes **Project Designer** seguindo as etapas fornecidas em [gerenciamento de projeto e propriedades da solução](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="49299-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="49299-131">Para definir constantes na linha de comando</span><span class="sxs-lookup"><span data-stu-id="49299-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="49299-132">-Usar o **/d** switch entre constantes de compilação condicional, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="49299-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="49299-133">Nenhum espaço é necessário entre a **/d** switch e a primeira constante.</span><span class="sxs-lookup"><span data-stu-id="49299-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="49299-134">Para obter mais informações, consulte [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="49299-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="49299-135">Declarações de linha de comando substituem declarações inseridas no **Project Designer**, mas não apaga-los.</span><span class="sxs-lookup"><span data-stu-id="49299-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="49299-136">Os argumentos definidos **Project Designer** permanecem em vigor para compilações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="49299-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="49299-137">Ao escrever constantes no próprio código, existem regras rígidas quanto seu posicionamento, como seu escopo é todo o módulo no qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="49299-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="49299-138">Definir constantes em seu código</span><span class="sxs-lookup"><span data-stu-id="49299-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="49299-139">-Coloca as constantes no bloco de declaração do módulo no qual eles são usados.</span><span class="sxs-lookup"><span data-stu-id="49299-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="49299-140">Isso ajuda a manter seu código organizados e fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="49299-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="49299-141">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="49299-141">Related Topics</span></span>  
  
|<span data-ttu-id="49299-142">Título</span><span class="sxs-lookup"><span data-stu-id="49299-142">Title</span></span>|<span data-ttu-id="49299-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="49299-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="49299-144">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="49299-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="49299-145">Fornece sugestões para tornar o seu código fácil de ler e manter.</span><span class="sxs-lookup"><span data-stu-id="49299-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="49299-146">Referência</span><span class="sxs-lookup"><span data-stu-id="49299-146">Reference</span></span>  
 [<span data-ttu-id="49299-147">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="49299-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="49299-148">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="49299-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="49299-149">/Define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49299-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
