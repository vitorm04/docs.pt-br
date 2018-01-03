---
title: "Instrução Option Explicit (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3d4c9cd3310e0ec3943c4e2b5e28be5b9a393db
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="946d0-102">Instrução Option Explicit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946d0-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="946d0-103">Força a declaração explícita de todas as variáveis em um arquivo ou permite declarações implícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="946d0-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="946d0-104">Syntax</span></span>  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="946d0-105">Partes</span><span class="sxs-lookup"><span data-stu-id="946d0-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="946d0-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="946d0-106">Optional.</span></span> <span data-ttu-id="946d0-107">Permite `Option Explicit` verificação.</span><span class="sxs-lookup"><span data-stu-id="946d0-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="946d0-108">Se `On` ou `Off` não for especificado, o padrão é `On`.</span><span class="sxs-lookup"><span data-stu-id="946d0-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="946d0-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="946d0-109">Optional.</span></span> <span data-ttu-id="946d0-110">Desabilita `Option Explicit` verificação.</span><span class="sxs-lookup"><span data-stu-id="946d0-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="946d0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="946d0-111">Remarks</span></span>  
 <span data-ttu-id="946d0-112">Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando a `Dim` ou `ReDim` instruções.</span><span class="sxs-lookup"><span data-stu-id="946d0-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="946d0-113">Se você tentar usar um nome de variável não declarado, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="946d0-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="946d0-114">O `Option Explicit Off` instrução permite que a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="946d0-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="946d0-115">Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="946d0-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="946d0-116">Configuração `Option Explicit` para `Off` geralmente não é uma prática recomendada.</span><span class="sxs-lookup"><span data-stu-id="946d0-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="946d0-117">Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.</span><span class="sxs-lookup"><span data-stu-id="946d0-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="946d0-118">Quando uma instrução Option Explicit não está presente</span><span class="sxs-lookup"><span data-stu-id="946d0-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="946d0-119">Se o código-fonte não contém um `Option Explicit` instrução, o **Option Explicit** definição no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado.</span><span class="sxs-lookup"><span data-stu-id="946d0-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="946d0-120">Se o compilador de linha de comando é usado, o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador é usada.</span><span class="sxs-lookup"><span data-stu-id="946d0-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="946d0-121">Para definir o Option Explicit no IDE</span><span class="sxs-lookup"><span data-stu-id="946d0-121">To set Option Explicit in the IDE</span></span>  
  
1.  <span data-ttu-id="946d0-122">No **Gerenciador de Soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="946d0-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="946d0-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="946d0-123">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="946d0-124">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="946d0-124">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="946d0-125">Definir o valor no **Option Explicit** caixa.</span><span class="sxs-lookup"><span data-stu-id="946d0-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="946d0-126">Quando você cria um novo projeto, o **Option Explicit** definição no **compilar** for definido como o **Option Explicit** definindo no **padrões de VB**caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="946d0-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="946d0-127">Para acessar o **padrões VB** caixa de diálogo de **ferramentas** menu, clique em **opções**.</span><span class="sxs-lookup"><span data-stu-id="946d0-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="946d0-128">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="946d0-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="946d0-129">A configuração inicial padrão na **padrões VB** é `On`.</span><span class="sxs-lookup"><span data-stu-id="946d0-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="946d0-130">Para definir o Option Explicit na linha de comando</span><span class="sxs-lookup"><span data-stu-id="946d0-130">To set Option Explicit on the command line</span></span>  
  
-   <span data-ttu-id="946d0-131">Incluir o [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) opção de compilador no **vbc** comando.</span><span class="sxs-lookup"><span data-stu-id="946d0-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="946d0-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="946d0-132">Example</span></span>  
 <span data-ttu-id="946d0-133">O exemplo a seguir usa o `Option Explicit` instrução para forçar a declaração explícita de todas as variáveis.</span><span class="sxs-lookup"><span data-stu-id="946d0-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="946d0-134">Tentativa de usar uma variável não declarada provoca um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="946d0-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="946d0-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="946d0-135">See Also</span></span>  
 [<span data-ttu-id="946d0-136">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="946d0-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="946d0-137">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="946d0-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="946d0-138">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="946d0-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="946d0-139">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="946d0-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="946d0-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="946d0-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="946d0-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="946d0-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="946d0-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="946d0-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="946d0-143">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="946d0-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
