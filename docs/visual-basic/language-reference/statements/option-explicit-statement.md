---
title: "Opção Explicit Statement (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
dev_langs:
- VB
helpviewer_keywords:
- declaring variables, explicit
- forced variable declaration in Option Explicit statement
- Explicit keyword
- explicit variable declaration
- Option Explicit statement
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
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
ms.openlocfilehash: 4283599d9ed2ad9075ab0b2f404f1a12a31437ec
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="53f7f-102">Instrução Option Explicit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53f7f-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="53f7f-103">Força a declaração explícita de todas as variáveis em um arquivo ou permite declarações implícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="53f7f-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f7f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53f7f-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="53f7f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="53f7f-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="53f7f-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="53f7f-106">Optional.</span></span> <span data-ttu-id="53f7f-107">Permite `Option Explicit` verificação.</span><span class="sxs-lookup"><span data-stu-id="53f7f-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="53f7f-108">Se `On` ou `Off` não for especificado, o padrão é `On`.</span><span class="sxs-lookup"><span data-stu-id="53f7f-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="53f7f-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="53f7f-109">Optional.</span></span> <span data-ttu-id="53f7f-110">Desabilita `Option Explicit` verificação.</span><span class="sxs-lookup"><span data-stu-id="53f7f-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53f7f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="53f7f-111">Remarks</span></span>  
 <span data-ttu-id="53f7f-112">Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando a `Dim` ou `ReDim` instruções.</span><span class="sxs-lookup"><span data-stu-id="53f7f-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="53f7f-113">Se você tentar usar um nome de variável não declarado, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="53f7f-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="53f7f-114">O `Option Explicit Off` instrução permite declarações implícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="53f7f-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="53f7f-115">Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="53f7f-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53f7f-116">Definindo `Option Explicit` para `Off` geralmente não é uma boa prática.</span><span class="sxs-lookup"><span data-stu-id="53f7f-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="53f7f-117">Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.</span><span class="sxs-lookup"><span data-stu-id="53f7f-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="53f7f-118">Quando uma instrução Option Explicit não está presente</span><span class="sxs-lookup"><span data-stu-id="53f7f-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="53f7f-119">Se o código-fonte não contém um `Option Explicit` instrução, o **Option Explicit** definição no [página de compilação, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado.</span><span class="sxs-lookup"><span data-stu-id="53f7f-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="53f7f-120">Se o compilador de linha de comando é usado, o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador é usada.</span><span class="sxs-lookup"><span data-stu-id="53f7f-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="53f7f-121">Para definir Option Explicit no IDE</span><span class="sxs-lookup"><span data-stu-id="53f7f-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="53f7f-122">Em **Solution Explorer**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="53f7f-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="53f7f-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="53f7f-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="53f7f-124">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="53f7f-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="53f7f-125">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="53f7f-125">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="53f7f-126">Defina o valor no **Option Explicit** caixa.</span><span class="sxs-lookup"><span data-stu-id="53f7f-126">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="53f7f-127">Quando você cria um novo projeto, o **Option Explicit** definição no **compilar** for definido como o **Option Explicit** definindo no **padrões de VB** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="53f7f-127">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="53f7f-128">Para acessar o **padrões de VB** caixa de diálogo de **ferramentas** menu, clique em **opções**.</span><span class="sxs-lookup"><span data-stu-id="53f7f-128">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="53f7f-129">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="53f7f-129">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="53f7f-130">A configuração inicial padrão em **padrões de VB** é `On`.</span><span class="sxs-lookup"><span data-stu-id="53f7f-130">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="53f7f-131">Para definir Option Explicit na linha de comando</span><span class="sxs-lookup"><span data-stu-id="53f7f-131">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="53f7f-132">Incluir o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador no **vbc** comando.</span><span class="sxs-lookup"><span data-stu-id="53f7f-132">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53f7f-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53f7f-133">Example</span></span>  
 <span data-ttu-id="53f7f-134">O exemplo a seguir usa o `Option Explicit` instrução para forçar a declaração explícita de todas as variáveis.</span><span class="sxs-lookup"><span data-stu-id="53f7f-134">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="53f7f-135">Tentativa de usar uma variável não declarada causa um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="53f7f-135">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 <span data-ttu-id="53f7f-136">[!code-vb[47 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="53f7f-136">[!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="53f7f-137">[!code-vb[48 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="53f7f-137">[!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f7f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53f7f-138">See Also</span></span>  
 <span data-ttu-id="53f7f-139">[Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-139">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="53f7f-140"> [Instrução reDim](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-140"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="53f7f-141"> [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-141"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="53f7f-142"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-142"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="53f7f-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-143"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="53f7f-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-144"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="53f7f-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="53f7f-145"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="53f7f-146"> [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="53f7f-146"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
