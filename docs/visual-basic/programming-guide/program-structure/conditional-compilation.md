---
title: "Compilação condicional no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- conditional compilation, about conditional compilation
- compilation, conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b0226f0d5ef6611acd44b2c12848bdf309c4ce32
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="93fd7-102">Compilação condicional no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93fd7-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="93fd7-103">Em *compilação condicional*, determinados blocos de código em um programa são compilados seletivamente, enquanto outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="93fd7-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="93fd7-104">Por exemplo, você talvez queira escrever declarações de depuração que comparam a velocidade das abordagens diferentes para a mesma tarefa de programação, ou você talvez queira localizar um aplicativo para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="93fd7-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="93fd7-105">Instruções de compilação condicional são projetadas para execução durante o tempo de compilação, não em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="93fd7-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="93fd7-106">Denota blocos de código para serem condicionalmente compilados com a `#If...Then...#Else` diretiva.</span><span class="sxs-lookup"><span data-stu-id="93fd7-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="93fd7-107">Por exemplo, para criar o francês e alemão versões do mesmo aplicativo no mesmo código-fonte, você deve inserir segmentos de código específico da plataforma em `#If...Then` instruções usando as constantes predefinidas `FrenchVersion` e `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="93fd7-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="93fd7-108">O exemplo a seguir demonstra como:</span><span class="sxs-lookup"><span data-stu-id="93fd7-108">The following example demonstrates how:</span></span>  
  
 <span data-ttu-id="93fd7-109">[!code-vb[VbVbalrConditionalComp n º&5;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="93fd7-109">[!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]</span></span>  
  
 <span data-ttu-id="93fd7-110">Se você definir o valor de `FrenchVersion` constante de compilação condicional para `True` em tempo de compilação, o código condicional para a versão em francês é compilado.</span><span class="sxs-lookup"><span data-stu-id="93fd7-110">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="93fd7-111">Se você definir o valor de `GermanVersion` constante para `True`, o compilador usará a versão em alemão.</span><span class="sxs-lookup"><span data-stu-id="93fd7-111">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="93fd7-112">Se nenhuma for configurada para `True`, o código no último `Else` bloco é executado.</span><span class="sxs-lookup"><span data-stu-id="93fd7-112">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93fd7-113">Preenchimento automático será não funcionará quando a edição de código e usando diretivas de compilação condicional, se o código não for parte da ramificação atual.</span><span class="sxs-lookup"><span data-stu-id="93fd7-113">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="93fd7-114">Declarando constantes de compilação condicional</span><span class="sxs-lookup"><span data-stu-id="93fd7-114">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="93fd7-115">Você pode definir constantes de compilação condicional em uma destas três maneiras:</span><span class="sxs-lookup"><span data-stu-id="93fd7-115">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="93fd7-116">No **Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="93fd7-116">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="93fd7-117">Na linha de comando ao usar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="93fd7-117">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="93fd7-118">Em seu código</span><span class="sxs-lookup"><span data-stu-id="93fd7-118">In your code</span></span>  
  
 <span data-ttu-id="93fd7-119">Constantes de compilação condicional tem um escopo especial e não podem ser acessados de código padrão.</span><span class="sxs-lookup"><span data-stu-id="93fd7-119">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="93fd7-120">O escopo de uma constante de compilação condicional é dependente da maneira que ele está definido.</span><span class="sxs-lookup"><span data-stu-id="93fd7-120">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="93fd7-121">A tabela a seguir lista o escopo das constantes declaradas usando cada uma das três maneiras mencionadas acima.</span><span class="sxs-lookup"><span data-stu-id="93fd7-121">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="93fd7-122">Configuração constante</span><span class="sxs-lookup"><span data-stu-id="93fd7-122">How constant is set</span></span>|<span data-ttu-id="93fd7-123">Escopo de constante</span><span class="sxs-lookup"><span data-stu-id="93fd7-123">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="93fd7-124">**Designer de projeto**</span><span class="sxs-lookup"><span data-stu-id="93fd7-124">**Project Designer**</span></span>|<span data-ttu-id="93fd7-125">Público para todos os arquivos do projeto</span><span class="sxs-lookup"><span data-stu-id="93fd7-125">Public to all files in the project</span></span>|  
|<span data-ttu-id="93fd7-126">Linha de comando</span><span class="sxs-lookup"><span data-stu-id="93fd7-126">Command line</span></span>|<span data-ttu-id="93fd7-127">Público para todos os arquivos são passados para o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="93fd7-127">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="93fd7-128">`#Const`instrução no código</span><span class="sxs-lookup"><span data-stu-id="93fd7-128">`#Const` statement in code</span></span>|<span data-ttu-id="93fd7-129">Para o arquivo no qual ela é declarada privada</span><span class="sxs-lookup"><span data-stu-id="93fd7-129">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="93fd7-130">Para definir constantes no Designer de projeto</span><span class="sxs-lookup"><span data-stu-id="93fd7-130">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="93fd7-131">-Antes de criar o arquivo executável, definir constantes no **Project Designer** seguindo as etapas fornecidas em [PONTA How to: modificar propriedades do projeto e definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).</span><span class="sxs-lookup"><span data-stu-id="93fd7-131">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).</span></span>|  
  
|<span data-ttu-id="93fd7-132">Para definir constantes na linha de comando</span><span class="sxs-lookup"><span data-stu-id="93fd7-132">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="93fd7-133">-Use o **/d** switch entre constantes de compilação condicional, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="93fd7-133">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="93fd7-134">Nenhum espaço é necessário entre a **/d** switch e a primeira constante.</span><span class="sxs-lookup"><span data-stu-id="93fd7-134">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="93fd7-135">Para obter mais informações, consulte [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="93fd7-135">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="93fd7-136">Declarações de linha de comando substituem declarações inseridas no **Project Designer**, mas não apaga-los.</span><span class="sxs-lookup"><span data-stu-id="93fd7-136">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="93fd7-137">Argumentos definidos **Project Designer** permanecerão em vigor para compilações subsequentes.</span><span class="sxs-lookup"><span data-stu-id="93fd7-137">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="93fd7-138">Ao escrever constantes no próprio código, existem regras rígidas quanto seu posicionamento, como seu escopo é todo o módulo no qual elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="93fd7-138">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="93fd7-139">Para definir constantes em seu código</span><span class="sxs-lookup"><span data-stu-id="93fd7-139">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="93fd7-140">-Coloque as constantes no bloco de declaração do módulo no qual eles são usados.</span><span class="sxs-lookup"><span data-stu-id="93fd7-140">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="93fd7-141">Isso ajuda a manter seu código mais fácil de ler e organizado.</span><span class="sxs-lookup"><span data-stu-id="93fd7-141">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="93fd7-142">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="93fd7-142">Related Topics</span></span>  
  
|<span data-ttu-id="93fd7-143">Título</span><span class="sxs-lookup"><span data-stu-id="93fd7-143">Title</span></span>|<span data-ttu-id="93fd7-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="93fd7-144">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="93fd7-145">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="93fd7-145">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="93fd7-146">Fornece sugestões para tornar seu código fácil de ler e manter.</span><span class="sxs-lookup"><span data-stu-id="93fd7-146">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="93fd7-147">Referência</span><span class="sxs-lookup"><span data-stu-id="93fd7-147">Reference</span></span>  
 [<span data-ttu-id="93fd7-148">Diretiva #Const</span><span class="sxs-lookup"><span data-stu-id="93fd7-148">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="93fd7-149">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="93fd7-149">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="93fd7-150">/Define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93fd7-150">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
