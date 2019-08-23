---
title: Compilação condicional no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 1bee64568ff92468e29226a395f7e5335387e256
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945579"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="10de8-102">Compilação condicional no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10de8-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="10de8-103">Na *compilação condicional*, blocos específicos de código em um programa são compilados seletivamente enquanto outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="10de8-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="10de8-104">Por exemplo, você pode querer escrever instruções de depuração que comparam a velocidade de diferentes abordagens para a mesma tarefa de programação ou pode desejar localizar um aplicativo para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="10de8-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="10de8-105">As instruções de compilação condicional são projetadas para serem executadas durante o tempo de compilação, não em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="10de8-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="10de8-106">Você denota que blocos de código sejam compilados condicionalmente com `#If...Then...#Else` a diretiva.</span><span class="sxs-lookup"><span data-stu-id="10de8-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="10de8-107">Por exemplo, para criar versões de idioma francês e alemão do mesmo aplicativo a partir do mesmo código-fonte, você insere segmentos de código específicos da plataforma `#If...Then` em instruções usando as constantes `FrenchVersion` predefinidas e `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="10de8-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="10de8-108">O exemplo a seguir demonstra como:</span><span class="sxs-lookup"><span data-stu-id="10de8-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="10de8-109">Se você definir o valor da `FrenchVersion` constante de compilação condicional como `True` em tempo de compilação, o código condicional para a versão em francês será compilado.</span><span class="sxs-lookup"><span data-stu-id="10de8-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="10de8-110">Se você definir o valor da `GermanVersion` constante como, o compilador usará a versão em `True`alemão.</span><span class="sxs-lookup"><span data-stu-id="10de8-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="10de8-111">Se nenhum for definido como `True`, o código no último `Else` bloco será executado.</span><span class="sxs-lookup"><span data-stu-id="10de8-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10de8-112">O preenchimento automático não funcionará ao editar o código e usar diretivas de compilação condicionais se o código não fizer parte do Branch atual.</span><span class="sxs-lookup"><span data-stu-id="10de8-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="10de8-113">Declarando constantes de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="10de8-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="10de8-114">Você pode definir constantes de compilação condicional de uma das três maneiras:</span><span class="sxs-lookup"><span data-stu-id="10de8-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="10de8-115">No **Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="10de8-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="10de8-116">Na linha de comando ao usar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="10de8-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="10de8-117">Em seu código</span><span class="sxs-lookup"><span data-stu-id="10de8-117">In your code</span></span>  
  
 <span data-ttu-id="10de8-118">As constantes de compilação condicional têm um escopo especial e não podem ser acessadas do código padrão.</span><span class="sxs-lookup"><span data-stu-id="10de8-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="10de8-119">O escopo de uma constante de compilação condicional depende da maneira como ela é definida.</span><span class="sxs-lookup"><span data-stu-id="10de8-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="10de8-120">A tabela a seguir lista o escopo de constantes declaradas usando cada uma das três formas mencionadas acima.</span><span class="sxs-lookup"><span data-stu-id="10de8-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="10de8-121">Como a constante é definida</span><span class="sxs-lookup"><span data-stu-id="10de8-121">How constant is set</span></span>|<span data-ttu-id="10de8-122">Escopo da constante</span><span class="sxs-lookup"><span data-stu-id="10de8-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="10de8-123">**Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="10de8-123">**Project Designer**</span></span>|<span data-ttu-id="10de8-124">Público para todos os arquivos no projeto</span><span class="sxs-lookup"><span data-stu-id="10de8-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="10de8-125">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="10de8-125">Command line</span></span>|<span data-ttu-id="10de8-126">Público para todos os arquivos passados para o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="10de8-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="10de8-127">`#Const`instrução no código</span><span class="sxs-lookup"><span data-stu-id="10de8-127">`#Const` statement in code</span></span>|<span data-ttu-id="10de8-128">Privado para o arquivo no qual ele está declarado</span><span class="sxs-lookup"><span data-stu-id="10de8-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="10de8-129">Para definir constantes no designer de projeto</span><span class="sxs-lookup"><span data-stu-id="10de8-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="10de8-130">-Antes de criar o arquivo executável, defina constantes no **Designer de projeto** seguindo as etapas fornecidas em [Gerenciando as propriedades do projeto e da solução](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="10de8-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="10de8-131">Para definir constantes na linha de comando</span><span class="sxs-lookup"><span data-stu-id="10de8-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="10de8-132">-Use a opção **/d** para inserir constantes de compilação condicional, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10de8-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="10de8-133">Nenhum espaço é necessário entre a opção **/d** e a primeira constante.</span><span class="sxs-lookup"><span data-stu-id="10de8-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="10de8-134">Para obter mais informações, consulte [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="10de8-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="10de8-135">Declarações de linha de comando substituem declarações inseridas no **Designer de projeto**, mas não as apagam.</span><span class="sxs-lookup"><span data-stu-id="10de8-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="10de8-136">Os argumentos definidos no **Designer de projeto** permanecem em vigor para compilações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="10de8-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="10de8-137">Ao escrever constantes no próprio código, não há regras estritas em seu posicionamento, pois seu escopo é o módulo inteiro no qual elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="10de8-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="10de8-138">Para definir constantes em seu código</span><span class="sxs-lookup"><span data-stu-id="10de8-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="10de8-139">-Coloque as constantes no bloco de declaração do módulo no qual elas são usadas.</span><span class="sxs-lookup"><span data-stu-id="10de8-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="10de8-140">Isso ajuda a manter seu código organizado e mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="10de8-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="10de8-141">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="10de8-141">Related Topics</span></span>  
  
|<span data-ttu-id="10de8-142">Título</span><span class="sxs-lookup"><span data-stu-id="10de8-142">Title</span></span>|<span data-ttu-id="10de8-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="10de8-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="10de8-144">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="10de8-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="10de8-145">Fornece sugestões para tornar seu código fácil de ler e manter.</span><span class="sxs-lookup"><span data-stu-id="10de8-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="10de8-146">Referência</span><span class="sxs-lookup"><span data-stu-id="10de8-146">Reference</span></span>  
 [<span data-ttu-id="10de8-147">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="10de8-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="10de8-148">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="10de8-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="10de8-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10de8-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
