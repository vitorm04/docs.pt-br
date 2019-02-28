---
title: Compilação condicional no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 828edf2e5491394f5ac802b5c9babfb3df359e59
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967836"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="0fef2-102">Compilação condicional no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0fef2-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="0fef2-103">Na *compilação condicional*, blocos específicos de código em um programa são compilados seletivamente, enquanto outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="0fef2-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="0fef2-104">Por exemplo, você talvez queira escrever declarações de depuração que comparam a velocidade das diferentes abordagens para a mesma tarefa de programação, ou você talvez queira localizar um aplicativo para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="0fef2-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="0fef2-105">Instruções de compilação condicional são projetadas para execução durante o tempo de compilação, não em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0fef2-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="0fef2-106">Você denota blocos de código seja compilado condicionalmente com o `#If...Then...#Else` diretiva.</span><span class="sxs-lookup"><span data-stu-id="0fef2-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="0fef2-107">Por exemplo, para criar o francês e alemão versões do mesmo aplicativo no mesmo código-fonte, você deve inserir segmentos de código específico da plataforma na `#If...Then` instruções usando as constantes predefinidas `FrenchVersion` e `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="0fef2-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="0fef2-108">O exemplo a seguir demonstra como:</span><span class="sxs-lookup"><span data-stu-id="0fef2-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="0fef2-109">Se você definir o valor da `FrenchVersion` constante de compilação condicional para `True` em tempo de compilação, o código condicional para a versão em francês é compilado.</span><span class="sxs-lookup"><span data-stu-id="0fef2-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="0fef2-110">Se você definir o valor de `GermanVersion` constante a ser `True`, o compilador usa a versão em alemão.</span><span class="sxs-lookup"><span data-stu-id="0fef2-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="0fef2-111">Se nenhum dos dois for definido como `True`, o código no último `Else` execução do bloco.</span><span class="sxs-lookup"><span data-stu-id="0fef2-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fef2-112">Preenchimento automático será não funcionará quando a edição de código e usar diretivas de compilação condicional, se o código não faz parte do branch atual.</span><span class="sxs-lookup"><span data-stu-id="0fef2-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="0fef2-113">Declarando constantes de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="0fef2-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="0fef2-114">Você pode definir as constantes de compilação condicional em uma das três maneiras:</span><span class="sxs-lookup"><span data-stu-id="0fef2-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="0fef2-115">No **Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="0fef2-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="0fef2-116">Na linha de comando ao usar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="0fef2-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="0fef2-117">Em seu código</span><span class="sxs-lookup"><span data-stu-id="0fef2-117">In your code</span></span>  
  
 <span data-ttu-id="0fef2-118">Constantes de compilação condicional têm um escopo especial e não podem ser acessados de código padrão.</span><span class="sxs-lookup"><span data-stu-id="0fef2-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="0fef2-119">O escopo de uma constante de compilação condicional é dependendo da forma que ele está definido.</span><span class="sxs-lookup"><span data-stu-id="0fef2-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="0fef2-120">A tabela a seguir lista o escopo das constantes declaradas usando cada uma das três maneiras mencionadas acima.</span><span class="sxs-lookup"><span data-stu-id="0fef2-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="0fef2-121">Como a constante é definida</span><span class="sxs-lookup"><span data-stu-id="0fef2-121">How constant is set</span></span>|<span data-ttu-id="0fef2-122">Escopo de constante</span><span class="sxs-lookup"><span data-stu-id="0fef2-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="0fef2-123">**Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="0fef2-123">**Project Designer**</span></span>|<span data-ttu-id="0fef2-124">Público para todos os arquivos no projeto</span><span class="sxs-lookup"><span data-stu-id="0fef2-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="0fef2-125">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="0fef2-125">Command line</span></span>|<span data-ttu-id="0fef2-126">Público para todos os arquivos passados para o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="0fef2-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="0fef2-127">`#Const` instrução no código</span><span class="sxs-lookup"><span data-stu-id="0fef2-127">`#Const` statement in code</span></span>|<span data-ttu-id="0fef2-128">Privado para o arquivo no qual ela é declarada</span><span class="sxs-lookup"><span data-stu-id="0fef2-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="0fef2-129">Para definir constantes no Designer de projeto</span><span class="sxs-lookup"><span data-stu-id="0fef2-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="0fef2-130">-A antes de criar seu arquivo executável, definir constantes na **Designer de projeto** seguindo as etapas fornecidas [propriedades de solução e gerenciando projetos](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="0fef2-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="0fef2-131">Para definir constantes na linha de comando</span><span class="sxs-lookup"><span data-stu-id="0fef2-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="0fef2-132">– Use o **/d** switch para inserir as constantes de compilação condicional, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0fef2-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="0fef2-133">Nenhum espaço é necessário entre o **/d** switch e a primeira constante.</span><span class="sxs-lookup"><span data-stu-id="0fef2-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="0fef2-134">Para obter mais informações, consulte [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="0fef2-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="0fef2-135">Declarações de linha de comando substituem as declarações inseridas na **Designer de projeto**, mas não apagados.</span><span class="sxs-lookup"><span data-stu-id="0fef2-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="0fef2-136">Argumentos definidos **Designer de projeto** permanecem em vigor para as compilações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="0fef2-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="0fef2-137">Ao escrever constantes no próprio código, existem regras rígidas sobre seu posicionamento, como seu escopo é todo o módulo no qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="0fef2-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="0fef2-138">Para definir constantes em seu código</span><span class="sxs-lookup"><span data-stu-id="0fef2-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="0fef2-139">-Coloque as constantes no bloco de declaração do módulo no qual eles são usados.</span><span class="sxs-lookup"><span data-stu-id="0fef2-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="0fef2-140">Isso ajuda a manter seu código organizado e fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="0fef2-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="0fef2-141">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="0fef2-141">Related Topics</span></span>  
  
|<span data-ttu-id="0fef2-142">Título</span><span class="sxs-lookup"><span data-stu-id="0fef2-142">Title</span></span>|<span data-ttu-id="0fef2-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fef2-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="0fef2-144">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="0fef2-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="0fef2-145">Fornece sugestões para tornar mais fácil de ler e manter o seu código.</span><span class="sxs-lookup"><span data-stu-id="0fef2-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="0fef2-146">Referência</span><span class="sxs-lookup"><span data-stu-id="0fef2-146">Reference</span></span>  
 [<span data-ttu-id="0fef2-147">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="0fef2-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="0fef2-148">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="0fef2-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="0fef2-149">/Define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fef2-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
