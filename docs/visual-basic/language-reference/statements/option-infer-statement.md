---
title: "Instrução Option Infer | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OptionInfer
- vb.Infer
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement
- Infer keyword
- declaring variables, inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
caps.latest.revision: 72
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
ms.openlocfilehash: 56c2813f0fcfc23c4eb4039ffbbb1d9deeccb72c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="option-infer-statement"></a><span data-ttu-id="82065-102">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="82065-102">Option Infer Statement</span></span>
<span data-ttu-id="82065-103">Permite o uso de inferência de tipo local ao declarar variáveis.</span><span class="sxs-lookup"><span data-stu-id="82065-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82065-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82065-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="82065-105">Partes</span><span class="sxs-lookup"><span data-stu-id="82065-105">Parts</span></span>  
  
|<span data-ttu-id="82065-106">Termo</span><span class="sxs-lookup"><span data-stu-id="82065-106">Term</span></span>|<span data-ttu-id="82065-107">Definição</span><span class="sxs-lookup"><span data-stu-id="82065-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="82065-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="82065-108">Optional.</span></span> <span data-ttu-id="82065-109">Permite inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="82065-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="82065-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="82065-110">Optional.</span></span> <span data-ttu-id="82065-111">Desabilita inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="82065-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82065-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="82065-112">Remarks</span></span>  
 <span data-ttu-id="82065-113">Para definir `Option Infer` em um arquivo, digite `Option Infer On` ou `Option Infer Off` na parte superior do arquivo, antes de qualquer outro código-fonte.</span><span class="sxs-lookup"><span data-stu-id="82065-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="82065-114">Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.</span><span class="sxs-lookup"><span data-stu-id="82065-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="82065-115">Quando você define `Option Infer` para `On`, você pode declarar variáveis locais sem especificar explicitamente um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="82065-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="82065-116">O compilador infere o tipo de dados de uma variável do tipo de sua expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="82065-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="82065-117">Na ilustração a seguir, `Option Infer` está ativado.</span><span class="sxs-lookup"><span data-stu-id="82065-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="82065-118">A variável na declaração `Dim someVar = 2` é declarada como um inteiro por inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="82065-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="82065-119">![Exibição do IntelliSense da declaração.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="82065-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="82065-120">IntelliSense quando o Option Infer está ligado</span><span class="sxs-lookup"><span data-stu-id="82065-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="82065-121">Na ilustração a seguir, o `Option Infer` está desativado.</span><span class="sxs-lookup"><span data-stu-id="82065-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="82065-122">A variável na declaração `Dim someVar = 2` é declarada como um `Object` por inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="82065-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="82065-123">Neste exemplo, o **Option Strict** configuração é definida como **Off** no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="82065-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="82065-124">![Exibição do IntelliSense da declaração.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="82065-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="82065-125">IntelliSense quando o Option Infer está desligado</span><span class="sxs-lookup"><span data-stu-id="82065-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82065-126">Quando uma variável é declarada como um `Object`, o tipo de tempo de execução pode ser alterado enquanto o programa está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="82065-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="82065-127">executa operações chamadas *conversão boxing* e *unboxing* para converter entre um `Object` e um tipo de valor, o que torna a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="82065-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="82065-128">Para obter informações sobre conversões boxing e unboxing, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification.md).</span><span class="sxs-lookup"><span data-stu-id="82065-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).</span></span>  
  
 <span data-ttu-id="82065-129">A inferência de tipo aplica-se no nível do procedimento e não fora de um procedimento em uma classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="82065-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="82065-130">Para obter informações adicionais, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="82065-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="82065-131">Quando uma Instrução Option Infer Não Está Presente</span><span class="sxs-lookup"><span data-stu-id="82065-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="82065-132">Se o código-fonte não contém um `Option Infer` instrução, o **Option Infer** definição no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado.</span><span class="sxs-lookup"><span data-stu-id="82065-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="82065-133">Se o compilador de linha de comando é usado, o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador é usada.</span><span class="sxs-lookup"><span data-stu-id="82065-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="82065-134">Para definir o Option Infer no IDE</span><span class="sxs-lookup"><span data-stu-id="82065-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="82065-135">Em **Solution Explorer**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="82065-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="82065-136">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="82065-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="82065-137">Para obter mais informações, consulte [NIB: Gerenciando propriedades do projeto com o Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="82065-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="82065-138">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="82065-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="82065-139">Defina o valor no **Option infer** caixa.</span><span class="sxs-lookup"><span data-stu-id="82065-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="82065-140">Quando você cria um novo projeto, o **Option Infer** definição no **compilar** for definido como o **Option Infer** definindo no **padrões de VB** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="82065-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="82065-141">Para acessar o **padrões de VB** caixa de diálogo de **ferramentas** menu, clique em **opções**.</span><span class="sxs-lookup"><span data-stu-id="82065-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="82065-142">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="82065-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="82065-143">A configuração inicial padrão em **padrões de VB** é `On`.</span><span class="sxs-lookup"><span data-stu-id="82065-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="82065-144">Para definir o Option Infer na linha de comando</span><span class="sxs-lookup"><span data-stu-id="82065-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="82065-145">Incluir o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador no **vbc** comando.</span><span class="sxs-lookup"><span data-stu-id="82065-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="82065-146">Tipos de Dados e Valores Padrão</span><span class="sxs-lookup"><span data-stu-id="82065-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="82065-147">A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.</span><span class="sxs-lookup"><span data-stu-id="82065-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="82065-148">Tipo de dados especificado?</span><span class="sxs-lookup"><span data-stu-id="82065-148">Data type specified?</span></span>|<span data-ttu-id="82065-149">Inicializador especificado?</span><span class="sxs-lookup"><span data-stu-id="82065-149">Initializer specified?</span></span>|<span data-ttu-id="82065-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82065-150">Example</span></span>|<span data-ttu-id="82065-151">Resultado</span><span class="sxs-lookup"><span data-stu-id="82065-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="82065-152">Não</span><span class="sxs-lookup"><span data-stu-id="82065-152">No</span></span>|<span data-ttu-id="82065-153">Não</span><span class="sxs-lookup"><span data-stu-id="82065-153">No</span></span>|`Dim qty`|<span data-ttu-id="82065-154">Se o `Option Strict` estiver desativado (padrão), a variável é definida como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="82065-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="82065-155">Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="82065-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="82065-156">Não</span><span class="sxs-lookup"><span data-stu-id="82065-156">No</span></span>|<span data-ttu-id="82065-157">Sim</span><span class="sxs-lookup"><span data-stu-id="82065-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="82065-158">Se `Option Infer` estiver ativado (padrão), a variável usa o tipo de dados do inicializador.</span><span class="sxs-lookup"><span data-stu-id="82065-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="82065-159">Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="82065-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="82065-160">Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.</span><span class="sxs-lookup"><span data-stu-id="82065-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="82065-161">Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="82065-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="82065-162">Sim</span><span class="sxs-lookup"><span data-stu-id="82065-162">Yes</span></span>|<span data-ttu-id="82065-163">Não</span><span class="sxs-lookup"><span data-stu-id="82065-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="82065-164">A variável é inicializada para o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="82065-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="82065-165">Para obter mais informações, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="82065-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="82065-166">Sim</span><span class="sxs-lookup"><span data-stu-id="82065-166">Yes</span></span>|<span data-ttu-id="82065-167">Sim</span><span class="sxs-lookup"><span data-stu-id="82065-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="82065-168">Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="82065-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82065-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82065-169">Example</span></span>  
 <span data-ttu-id="82065-170">Os exemplos a seguir demonstram como a instrução `Option Infer` habilita a inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="82065-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 <span data-ttu-id="82065-171">[!code-vb[VbVbalrTypeInference n º&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="82065-171">[!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="82065-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82065-172">Example</span></span>  
 <span data-ttu-id="82065-173">O exemplo a seguir demonstra o tipo de tempo de execução pode ser diferente quando uma variável é identificada como um `Object`.</span><span class="sxs-lookup"><span data-stu-id="82065-173">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 <span data-ttu-id="82065-174">[!code-vb[VbVbalrTypeInference n º&11;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="82065-174">[!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82065-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82065-175">See Also</span></span>  
 <span data-ttu-id="82065-176">[Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="82065-176">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="82065-177"> [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="82065-177"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="82065-178"> [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="82065-178"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="82065-179"> [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="82065-179"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="82065-180"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="82065-180"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="82065-181"> [Caixa de diálogo de opções de padrões, projetos do Visual Basic](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span><span class="sxs-lookup"><span data-stu-id="82065-181"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box) </span></span>  
<span data-ttu-id="82065-182"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="82065-182"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="82065-183"> [Conversão boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)</span><span class="sxs-lookup"><span data-stu-id="82065-183"> [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)</span></span>
