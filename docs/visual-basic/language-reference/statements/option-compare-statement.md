---
title: Instrução Option Compare
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 7538466c8f4b90e2e655a2ec762d8c545546a481
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344422"
---
# <a name="option-compare-statement"></a><span data-ttu-id="ea0a2-102">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="ea0a2-102">Option Compare Statement</span></span>
<span data-ttu-id="ea0a2-103">Declara o método padrão de comparação a ser usado ao comparar dados da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea0a2-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="ea0a2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ea0a2-105">Parts</span></span>  
  
|<span data-ttu-id="ea0a2-106">Termo</span><span class="sxs-lookup"><span data-stu-id="ea0a2-106">Term</span></span>|<span data-ttu-id="ea0a2-107">Definição</span><span class="sxs-lookup"><span data-stu-id="ea0a2-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="ea0a2-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-108">Optional.</span></span> <span data-ttu-id="ea0a2-109">Resulta em comparações de cadeias de caracteres com base em uma ordem de classificação derivada das representações binárias internas dos caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="ea0a2-110">Esse tipo de comparação é útil principalmente se as cadeias de caracteres puderem conter caracteres que não serão interpretados como texto.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="ea0a2-111">Nesse caso, você não deseja ajustar comparações com equivalentes em ordem alfabética, como maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="ea0a2-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-112">Optional.</span></span> <span data-ttu-id="ea0a2-113">Resulta em comparações de cadeias de caracteres com base em uma ordem de classificação de texto com diferenciação de maiúsculas de minúsculas determinada pela localidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="ea0a2-114">Esse tipo de comparação é útil se suas cadeias de caracteres tiverem todos os caracteres de texto e você desejar compará-las levando em conta equivalências alfabéticas como maiúsculas e minúsculas e letras relacionadas.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="ea0a2-115">Por exemplo, você pode desejar considerar que `A` e `a` sejam iguais, e que `Ä` e `ä` venham antes de `B` e `b`.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea0a2-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea0a2-116">Remarks</span></span>  
 <span data-ttu-id="ea0a2-117">Se usado, a instrução `Option Compare` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="ea0a2-118">A instrução `Option Compare` especifica o método de comparação de cadeia de caracteres (`Binary` ou `Text`).</span><span class="sxs-lookup"><span data-stu-id="ea0a2-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="ea0a2-119">O método de comparação de texto padrão é `Binary`.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="ea0a2-120">A comparação `Binary` compara o valor de Unicode numérico de cada caractere em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="ea0a2-121">A comparação `Text` compara cada caractere Unicode com base em seu sentido lexical na cultura atual.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="ea0a2-122">No Microsoft Windows, a ordem de classificação é determinada pela página de código.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="ea0a2-123">Para obter mais informações, consulte [Páginas de Código](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="ea0a2-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="ea0a2-124">No exemplo a seguir, os caracteres na página de código Inglês/Europeu (ANSI 1252) são classificados usando `Option Compare Binary`, que produz uma ordem de classificação binária típica.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="ea0a2-125">Quando os mesmos caracteres na mesma página de código são classificados usando `Option Compare Text`, a ordem de classificação a seguir é produzida.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="ea0a2-126">Quando uma Instrução Option Compare Não Está Presente</span><span class="sxs-lookup"><span data-stu-id="ea0a2-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="ea0a2-127">Se o código-fonte não contiver uma instrução `Option Compare`, a **opção comparar** configuração na [página compilar, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) será usada.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="ea0a2-128">Se você usar o compilador de linha de comando, a configuração especificada pela opção de compilador [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) será usada.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="ea0a2-129">Para definir o Option Compare no IDE</span><span class="sxs-lookup"><span data-stu-id="ea0a2-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="ea0a2-130">No **Gerenciador de Soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="ea0a2-131">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="ea0a2-132">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="ea0a2-133">Defina o valor na caixa de **comparação de opções** .</span><span class="sxs-lookup"><span data-stu-id="ea0a2-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="ea0a2-134">Quando você cria um projeto, a **opção comparar** configuração na guia **Compilar** é definida como a **opção comparar** configuração na caixa de diálogo **Opções** .</span><span class="sxs-lookup"><span data-stu-id="ea0a2-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="ea0a2-135">Para alterar essa configuração, no menu **ferramentas** , clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="ea0a2-136">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="ea0a2-137">A configuração padrão inicial em **padrões do VB** é **Binary**.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="ea0a2-138">Para definir o Option Compare na linha de comando</span><span class="sxs-lookup"><span data-stu-id="ea0a2-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="ea0a2-139">Inclua a opção de compilador [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) no comando **Vbc** .</span><span class="sxs-lookup"><span data-stu-id="ea0a2-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea0a2-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea0a2-140">Example</span></span>  
 <span data-ttu-id="ea0a2-141">O exemplo a seguir usa a instrução `Option Compare` para definir a comparação binária como o método padrão de comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="ea0a2-142">Para usar esse código, retire os comentários da instrução `Option Compare Binary` e coloque-os na parte superior do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="ea0a2-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea0a2-143">Example</span></span>  
 <span data-ttu-id="ea0a2-144">O exemplo a seguir usa a instrução `Option Compare` para definir a ordem de classificação sem diferenciação de maiúsculas de minúsculas como o método padrão de comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="ea0a2-145">Para usar esse código, retire os comentários da instrução `Option Compare Text` e coloque-os na parte superior do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="ea0a2-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="ea0a2-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea0a2-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="ea0a2-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="ea0a2-147">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="ea0a2-148">Operadores de Comparação</span><span class="sxs-lookup"><span data-stu-id="ea0a2-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="ea0a2-149">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea0a2-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="ea0a2-150">Operador Like</span><span class="sxs-lookup"><span data-stu-id="ea0a2-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="ea0a2-151">Funções da Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ea0a2-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="ea0a2-152">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="ea0a2-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="ea0a2-153">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="ea0a2-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
