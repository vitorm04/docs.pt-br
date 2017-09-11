---
title: "Instrução Option Compare | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 00618cd914c06b896d68b4074464af866f747895
ms.contentlocale: pt-br
ms.lasthandoff: 05/26/2017

---
# <a name="option-compare-statement"></a><span data-ttu-id="62b70-102">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="62b70-102">Option Compare Statement</span></span>
<span data-ttu-id="62b70-103">Declara o método padrão de comparação a ser usado ao comparar dados da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="62b70-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b70-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62b70-104">Syntax</span></span>  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="62b70-105">Partes</span><span class="sxs-lookup"><span data-stu-id="62b70-105">Parts</span></span>  
  
|<span data-ttu-id="62b70-106">Termo</span><span class="sxs-lookup"><span data-stu-id="62b70-106">Term</span></span>|<span data-ttu-id="62b70-107">Definição</span><span class="sxs-lookup"><span data-stu-id="62b70-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="62b70-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="62b70-108">Optional.</span></span> <span data-ttu-id="62b70-109">Resulta em comparações de cadeias de caracteres com base em uma ordem de classificação derivada das representações binárias internas dos caracteres.</span><span class="sxs-lookup"><span data-stu-id="62b70-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="62b70-110">Esse tipo de comparação é útil principalmente se as cadeias de caracteres puderem conter caracteres que não serão interpretados como texto.</span><span class="sxs-lookup"><span data-stu-id="62b70-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="62b70-111">Nesse caso, você não deseja ajustar comparações com equivalentes em ordem alfabética, como maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="62b70-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="62b70-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="62b70-112">Optional.</span></span> <span data-ttu-id="62b70-113">Resulta em comparações de cadeias de caracteres com base em uma ordem de classificação de texto com diferenciação de maiúsculas de minúsculas determinada pela localidade do sistema.</span><span class="sxs-lookup"><span data-stu-id="62b70-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="62b70-114">Esse tipo de comparação é útil se suas cadeias de caracteres tiverem todos os caracteres de texto e você desejar compará-las levando em conta equivalências alfabéticas como maiúsculas e minúsculas e letras relacionadas.</span><span class="sxs-lookup"><span data-stu-id="62b70-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="62b70-115">Por exemplo, você pode desejar considerar que `A` e `a` sejam iguais, e que `Ä` e `ä` venham antes de `B` e `b`.</span><span class="sxs-lookup"><span data-stu-id="62b70-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62b70-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="62b70-116">Remarks</span></span>  
 <span data-ttu-id="62b70-117">Se usado, a instrução `Option Compare` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="62b70-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="62b70-118">A instrução `Option Compare` especifica o método de comparação de cadeia de caracteres (`Binary` ou `Text`).</span><span class="sxs-lookup"><span data-stu-id="62b70-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="62b70-119">O método de comparação de texto padrão é `Binary`.</span><span class="sxs-lookup"><span data-stu-id="62b70-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="62b70-120">A comparação `Binary` compara o valor de Unicode numérico de cada caractere em cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="62b70-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="62b70-121">A comparação `Text` compara cada caractere Unicode com base em seu sentido lexical na cultura atual.</span><span class="sxs-lookup"><span data-stu-id="62b70-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="62b70-122">No Microsoft Windows, a ordem de classificação é determinada pela página de código.</span><span class="sxs-lookup"><span data-stu-id="62b70-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="62b70-123">Para obter mais informações, consulte [Páginas de Código](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="62b70-123">For more information, see [Code Pages](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="62b70-124">No exemplo a seguir, os caracteres na página de código Inglês/Europeu (ANSI 1252) são classificados usando `Option Compare Binary`, que produz uma ordem de classificação binária típica.</span><span class="sxs-lookup"><span data-stu-id="62b70-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="62b70-125">Quando os mesmos caracteres na mesma página de código são classificados usando `Option Compare Text`, a ordem de classificação a seguir é produzida.</span><span class="sxs-lookup"><span data-stu-id="62b70-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="62b70-126">Quando uma Instrução Option Compare Não Está Presente</span><span class="sxs-lookup"><span data-stu-id="62b70-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="62b70-127">Se o código-fonte não contém um `Option Compare` instrução, o **Option Compare** definição no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado.</span><span class="sxs-lookup"><span data-stu-id="62b70-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="62b70-128">Se você usar o compilador de linha de comando, a configuração especificada pelo [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) opção de compilador é usada.</span><span class="sxs-lookup"><span data-stu-id="62b70-128">If you use the command-line compiler, the setting specified by the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="62b70-129">Para definir o Option Compare no IDE</span><span class="sxs-lookup"><span data-stu-id="62b70-129">To set Option Compare in the IDE</span></span>  
  
1.  <span data-ttu-id="62b70-130">Em **Solution Explorer**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="62b70-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="62b70-131">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="62b70-131">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="62b70-132">Para obter mais informações, consulte [NIB: Gerenciando propriedades do projeto com o Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="62b70-132">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="62b70-133">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="62b70-133">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="62b70-134">Defina o valor no **Option Compare** caixa.</span><span class="sxs-lookup"><span data-stu-id="62b70-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="62b70-135">Quando você cria um projeto, o **Option Compare** definição no **compilar** for definido como o **Option Compare** definindo no **opções** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="62b70-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="62b70-136">Para alterar essa configuração, no **ferramentas** menu, clique em **opções**.</span><span class="sxs-lookup"><span data-stu-id="62b70-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="62b70-137">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="62b70-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="62b70-138">A configuração inicial padrão em **padrões de VB** é **binário**.</span><span class="sxs-lookup"><span data-stu-id="62b70-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="62b70-139">Para definir o Option Compare na linha de comando</span><span class="sxs-lookup"><span data-stu-id="62b70-139">To set Option Compare on the command line</span></span>  
  
-   <span data-ttu-id="62b70-140">Incluir o [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) opção de compilador no **vbc** comando.</span><span class="sxs-lookup"><span data-stu-id="62b70-140">Include the [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62b70-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62b70-141">Example</span></span>  
 <span data-ttu-id="62b70-142">O exemplo a seguir usa a instrução `Option Compare` para definir a comparação binária como o método padrão de comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="62b70-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="62b70-143">Para usar esse código, retire os comentários da instrução `Option Compare Binary` e coloque-os na parte superior do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="62b70-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="62b70-144">[!code-vb[45 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="62b70-144">[!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="62b70-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62b70-145">Example</span></span>  
 <span data-ttu-id="62b70-146">O exemplo a seguir usa a instrução `Option Compare` para definir a ordem de classificação sem diferenciação de maiúsculas de minúsculas como o método padrão de comparação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="62b70-146">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="62b70-147">Para usar esse código, retire os comentários da instrução `Option Compare Text` e coloque-os na parte superior do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="62b70-147">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 <span data-ttu-id="62b70-148">[!code-vb[46 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="62b70-148">[!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b70-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62b70-149">See Also</span></span>  
 <span data-ttu-id="62b70-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A></span><span class="sxs-lookup"><span data-stu-id="62b70-150"><xref:Microsoft.VisualBasic.Strings.InStr%2A></span></span>   
 <span data-ttu-id="62b70-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span><span class="sxs-lookup"><span data-stu-id="62b70-151"><xref:Microsoft.VisualBasic.Strings.InStrRev%2A></span></span>   
 <span data-ttu-id="62b70-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A></span><span class="sxs-lookup"><span data-stu-id="62b70-152"><xref:Microsoft.VisualBasic.Strings.Replace%2A></span></span>   
 <span data-ttu-id="62b70-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="62b70-153"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="62b70-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A></span><span class="sxs-lookup"><span data-stu-id="62b70-154"><xref:Microsoft.VisualBasic.Strings.StrComp%2A></span></span>   
<span data-ttu-id="62b70-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="62b70-155"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="62b70-156"> [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="62b70-156"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="62b70-157"> [Operadores de comparação em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="62b70-157"> [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="62b70-158"> [Operador LIKE](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="62b70-158"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="62b70-159"> [Funções de cadeia de caracteres](../../../visual-basic/language-reference/functions/string-functions.md) </span><span class="sxs-lookup"><span data-stu-id="62b70-159"> [String Functions](../../../visual-basic/language-reference/functions/string-functions.md) </span></span>  
<span data-ttu-id="62b70-160"> [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="62b70-160"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="62b70-161"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="62b70-161"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
