---
title: Option Infer Statement (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: a85d8012eea14abe4ddcdb35fa154245894a7f97
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582938"
---
# <a name="option-infer-statement"></a><span data-ttu-id="22ff0-102">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="22ff0-102">Option Infer Statement</span></span>
<span data-ttu-id="22ff0-103">Permite o uso de inferência de tipo local ao declarar variáveis.</span><span class="sxs-lookup"><span data-stu-id="22ff0-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ff0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22ff0-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="22ff0-105">Partes</span><span class="sxs-lookup"><span data-stu-id="22ff0-105">Parts</span></span>  
  
|<span data-ttu-id="22ff0-106">Termo</span><span class="sxs-lookup"><span data-stu-id="22ff0-106">Term</span></span>|<span data-ttu-id="22ff0-107">Definição</span><span class="sxs-lookup"><span data-stu-id="22ff0-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="22ff0-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22ff0-108">Optional.</span></span> <span data-ttu-id="22ff0-109">Permite inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="22ff0-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="22ff0-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22ff0-110">Optional.</span></span> <span data-ttu-id="22ff0-111">Desabilita inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="22ff0-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22ff0-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="22ff0-112">Remarks</span></span>  
 <span data-ttu-id="22ff0-113">Para definir `Option Infer` em um arquivo, digite `Option Infer On` ou `Option Infer Off` na parte superior do arquivo, antes de qualquer outro código-fonte.</span><span class="sxs-lookup"><span data-stu-id="22ff0-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="22ff0-114">Se o valor definido para `Option Infer` em um arquivo entrar em conflito com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.</span><span class="sxs-lookup"><span data-stu-id="22ff0-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="22ff0-115">Quando você define `Option Infer` para `On`, você pode declarar variáveis locais sem especificar explicitamente um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="22ff0-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="22ff0-116">O compilador infere o tipo de dados de uma variável do tipo de sua expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="22ff0-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="22ff0-117">Na ilustração a seguir, `Option Infer` está ativado.</span><span class="sxs-lookup"><span data-stu-id="22ff0-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="22ff0-118">A variável na declaração `Dim someVar = 2` é declarada como um inteiro por inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="22ff0-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

 <span data-ttu-id="22ff0-119">Captura de tela a seguir mostra o IntelliSense quando Option Infer está ligado:</span><span class="sxs-lookup"><span data-stu-id="22ff0-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span> 
  
 ![Captura de tela mostrando o modo de exibição de IntelliSense quando Option Infer está ligado.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 <span data-ttu-id="22ff0-121">Na ilustração a seguir, o `Option Infer` está desativado.</span><span class="sxs-lookup"><span data-stu-id="22ff0-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="22ff0-122">A variável na declaração `Dim someVar = 2` é declarada como um `Object` por inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="22ff0-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="22ff0-123">Neste exemplo, o **Option Strict** configuração é definida como **Off** no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="22ff0-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="22ff0-124">Captura de tela a seguir mostra o IntelliSense quando Option Infer está desligado:</span><span class="sxs-lookup"><span data-stu-id="22ff0-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>
 
 ![Captura de tela mostrando o modo de exibição de IntelliSense quando Option Infer está desligado.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  <span data-ttu-id="22ff0-126">Quando uma variável é declarada como um `Object`, o tipo de tempo de execução pode ser alterado enquanto o programa está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="22ff0-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="22ff0-127">Visual Basic executa operações denominadas *conversão boxing* e *unboxing* para converter entre um `Object` e um tipo de valor, o que torna a execução mais lenta.</span><span class="sxs-lookup"><span data-stu-id="22ff0-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="22ff0-128">Para obter informações sobre conversões boxing e unboxing, consulte o [especificação da linguagem Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="22ff0-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>
  
 <span data-ttu-id="22ff0-129">A inferência de tipo aplica-se no nível do procedimento e não fora de um procedimento em uma classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="22ff0-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="22ff0-130">Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="22ff0-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="22ff0-131">Quando uma Instrução Option Infer Não Está Presente</span><span class="sxs-lookup"><span data-stu-id="22ff0-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="22ff0-132">Se o código-fonte não contiver uma `Option Infer` instrução, o **Option Infer** definindo no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado.</span><span class="sxs-lookup"><span data-stu-id="22ff0-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="22ff0-133">Se o compilador de linha de comando é usado, o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador é usada.</span><span class="sxs-lookup"><span data-stu-id="22ff0-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="22ff0-134">Para definir o Option Infer no IDE</span><span class="sxs-lookup"><span data-stu-id="22ff0-134">To set Option Infer in the IDE</span></span>  
  
1. <span data-ttu-id="22ff0-135">No **Gerenciador de Soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="22ff0-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="22ff0-136">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="22ff0-136">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="22ff0-137">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="22ff0-137">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="22ff0-138">Defina o valor na **Option infer** caixa.</span><span class="sxs-lookup"><span data-stu-id="22ff0-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="22ff0-139">Quando você cria um novo projeto, o **Option Infer** definindo na **compilar** for definido como o **Option Infer** definindo no **padrões de VB** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="22ff0-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="22ff0-140">Para acessar o **padrões de VB** caixa de diálogo do **ferramentas** menu, clique em **opções**.</span><span class="sxs-lookup"><span data-stu-id="22ff0-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="22ff0-141">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="22ff0-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="22ff0-142">A configuração inicial padrão nos **padrões de VB** é `On`.</span><span class="sxs-lookup"><span data-stu-id="22ff0-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="22ff0-143">Para definir o Option Infer na linha de comando</span><span class="sxs-lookup"><span data-stu-id="22ff0-143">To set Option Infer on the command line</span></span>  
  
- <span data-ttu-id="22ff0-144">Incluir o [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) opção de compilador na **vbc** comando.</span><span class="sxs-lookup"><span data-stu-id="22ff0-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="22ff0-145">Tipos de Dados e Valores Padrão</span><span class="sxs-lookup"><span data-stu-id="22ff0-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="22ff0-146">A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.</span><span class="sxs-lookup"><span data-stu-id="22ff0-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="22ff0-147">Tipo de dados especificado?</span><span class="sxs-lookup"><span data-stu-id="22ff0-147">Data type specified?</span></span>|<span data-ttu-id="22ff0-148">Inicializador especificado?</span><span class="sxs-lookup"><span data-stu-id="22ff0-148">Initializer specified?</span></span>|<span data-ttu-id="22ff0-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22ff0-149">Example</span></span>|<span data-ttu-id="22ff0-150">Resultado</span><span class="sxs-lookup"><span data-stu-id="22ff0-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="22ff0-151">Não</span><span class="sxs-lookup"><span data-stu-id="22ff0-151">No</span></span>|<span data-ttu-id="22ff0-152">Não</span><span class="sxs-lookup"><span data-stu-id="22ff0-152">No</span></span>|`Dim qty`|<span data-ttu-id="22ff0-153">Se o `Option Strict` estiver desativado (padrão), a variável é definida como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="22ff0-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="22ff0-154">Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="22ff0-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="22ff0-155">Não</span><span class="sxs-lookup"><span data-stu-id="22ff0-155">No</span></span>|<span data-ttu-id="22ff0-156">Sim</span><span class="sxs-lookup"><span data-stu-id="22ff0-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="22ff0-157">Se `Option Infer` estiver ativado (padrão), a variável usa o tipo de dados do inicializador.</span><span class="sxs-lookup"><span data-stu-id="22ff0-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="22ff0-158">Ver [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="22ff0-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="22ff0-159">Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.</span><span class="sxs-lookup"><span data-stu-id="22ff0-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="22ff0-160">Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="22ff0-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="22ff0-161">Sim</span><span class="sxs-lookup"><span data-stu-id="22ff0-161">Yes</span></span>|<span data-ttu-id="22ff0-162">Não</span><span class="sxs-lookup"><span data-stu-id="22ff0-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="22ff0-163">A variável é inicializada para o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="22ff0-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="22ff0-164">Para obter mais informações, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="22ff0-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="22ff0-165">Sim</span><span class="sxs-lookup"><span data-stu-id="22ff0-165">Yes</span></span>|<span data-ttu-id="22ff0-166">Sim</span><span class="sxs-lookup"><span data-stu-id="22ff0-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="22ff0-167">Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="22ff0-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="22ff0-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22ff0-168">Example</span></span>  
 <span data-ttu-id="22ff0-169">Os exemplos a seguir demonstram como a instrução `Option Infer` habilita a inferência de tipo local.</span><span class="sxs-lookup"><span data-stu-id="22ff0-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="22ff0-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22ff0-170">Example</span></span>  
 <span data-ttu-id="22ff0-171">O exemplo a seguir demonstra o tipo de tempo de execução pode ser diferente quando uma variável é identificada como um `Object`.</span><span class="sxs-lookup"><span data-stu-id="22ff0-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="22ff0-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22ff0-172">See also</span></span>

- [<span data-ttu-id="22ff0-173">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="22ff0-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="22ff0-174">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="22ff0-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="22ff0-175">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="22ff0-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="22ff0-176">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="22ff0-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="22ff0-177">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="22ff0-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="22ff0-178">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="22ff0-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="22ff0-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="22ff0-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="22ff0-180">Conversão boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="22ff0-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
