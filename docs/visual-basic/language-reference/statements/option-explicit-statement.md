---
title: Instrução Option Explicit (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 19ff8cf1dbcdb941e38f23be4cb68d3a5e5b83a8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582576"
---
# <a name="option-explicit-statement-visual-basic"></a><span data-ttu-id="734f1-102">Instrução Option Explicit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="734f1-102">Option Explicit Statement (Visual Basic)</span></span>
<span data-ttu-id="734f1-103">Força a declaração explícita de todas as variáveis em um arquivo ou permite declarações implícitas de variáveis.</span><span class="sxs-lookup"><span data-stu-id="734f1-103">Forces explicit declaration of all variables in a file, or allows implicit declarations of variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="734f1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="734f1-104">Syntax</span></span>  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="734f1-105">Partes</span><span class="sxs-lookup"><span data-stu-id="734f1-105">Parts</span></span>  
 `On`  
 <span data-ttu-id="734f1-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="734f1-106">Optional.</span></span> <span data-ttu-id="734f1-107">Habilita a verificação de `Option Explicit`.</span><span class="sxs-lookup"><span data-stu-id="734f1-107">Enables `Option Explicit` checking.</span></span> <span data-ttu-id="734f1-108">Se `On` ou `Off` não for especificado, o padrão será `On`.</span><span class="sxs-lookup"><span data-stu-id="734f1-108">If `On` or `Off` is not specified, the default is `On`.</span></span>  
  
 `Off`  
 <span data-ttu-id="734f1-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="734f1-109">Optional.</span></span> <span data-ttu-id="734f1-110">Desabilita a verificação de `Option Explicit`.</span><span class="sxs-lookup"><span data-stu-id="734f1-110">Disables `Option Explicit` checking.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="734f1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="734f1-111">Remarks</span></span>  
 <span data-ttu-id="734f1-112">Quando `Option Explicit On` ou `Option Explicit` aparece em um arquivo, você deve declarar explicitamente todas as variáveis usando as instruções `Dim` ou `ReDim`.</span><span class="sxs-lookup"><span data-stu-id="734f1-112">When `Option Explicit On` or `Option Explicit` appears in a file, you must explicitly declare all variables by using the `Dim` or `ReDim` statements.</span></span> <span data-ttu-id="734f1-113">Se você tentar usar um nome de variável não declarado, ocorrerá um erro no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="734f1-113">If you try to use an undeclared variable name, an error occurs at compile time.</span></span> <span data-ttu-id="734f1-114">A instrução `Option Explicit Off` permite a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="734f1-114">The `Option Explicit Off` statement allows implicit declaration of variables.</span></span>  
  
 <span data-ttu-id="734f1-115">Se usado, a instrução `Option Explicit` deve aparecer em um arquivo antes de quaisquer outras instruções de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="734f1-115">If used, the `Option Explicit` statement must appear in a file before any other source code statements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="734f1-116">A definição de `Option Explicit` para `Off` geralmente não é uma boa prática.</span><span class="sxs-lookup"><span data-stu-id="734f1-116">Setting `Option Explicit` to `Off` is generally not a good practice.</span></span> <span data-ttu-id="734f1-117">Você poderia digitar incorretamente um nome de variável em um ou mais locais, o que levaria a resultados inesperados na execução do programa.</span><span class="sxs-lookup"><span data-stu-id="734f1-117">You could misspell a variable name in one or more locations, which would cause unexpected results when the program is run.</span></span>  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a><span data-ttu-id="734f1-118">Quando uma instrução Option Explicit não está presente</span><span class="sxs-lookup"><span data-stu-id="734f1-118">When an Option Explicit Statement Is Not Present</span></span>  
 <span data-ttu-id="734f1-119">Se o código-fonte não contiver uma instrução `Option Explicit`, a opção de configuração **explícita** na [página compilar, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) será usada.</span><span class="sxs-lookup"><span data-stu-id="734f1-119">If the source code does not contain an `Option Explicit` statement, the **Option Explicit** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="734f1-120">Se o compilador de linha de comando for usado, a opção de compilador [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) será usada.</span><span class="sxs-lookup"><span data-stu-id="734f1-120">If the command-line compiler is used, the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-explicit-in-the-ide"></a><span data-ttu-id="734f1-121">Para definir a opção Explicit no IDE</span><span class="sxs-lookup"><span data-stu-id="734f1-121">To set Option Explicit in the IDE</span></span>  
  
1. <span data-ttu-id="734f1-122">No **Gerenciador de Soluções**, selecione um projeto.</span><span class="sxs-lookup"><span data-stu-id="734f1-122">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="734f1-123">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="734f1-123">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="734f1-124">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="734f1-124">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="734f1-125">Defina o valor na caixa **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="734f1-125">Set the value in the **Option Explicit** box.</span></span>  
  
 <span data-ttu-id="734f1-126">Quando você cria um novo projeto, a **opção configuração explícita** na guia **Compilar** é definida como a **opção configuração explícita** na caixa de diálogo **padrões do VB** .</span><span class="sxs-lookup"><span data-stu-id="734f1-126">When you create a new project, the **Option Explicit** setting on the **Compile** tab is set to the **Option Explicit** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="734f1-127">Para acessar a caixa de diálogo **padrões do VB** , no menu **ferramentas** , clique em **Opções**.</span><span class="sxs-lookup"><span data-stu-id="734f1-127">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="734f1-128">Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**.</span><span class="sxs-lookup"><span data-stu-id="734f1-128">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="734f1-129">A configuração padrão inicial em **padrões do VB** é `On`.</span><span class="sxs-lookup"><span data-stu-id="734f1-129">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a><span data-ttu-id="734f1-130">Para definir a opção Explicit na linha de comando</span><span class="sxs-lookup"><span data-stu-id="734f1-130">To set Option Explicit on the command line</span></span>  
  
- <span data-ttu-id="734f1-131">Inclua a opção de compilador [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) no comando **Vbc** .</span><span class="sxs-lookup"><span data-stu-id="734f1-131">Include the [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="734f1-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="734f1-132">Example</span></span>  
 <span data-ttu-id="734f1-133">O exemplo a seguir usa a instrução `Option Explicit` para forçar a declaração explícita de todas as variáveis.</span><span class="sxs-lookup"><span data-stu-id="734f1-133">The following example uses the `Option Explicit` statement to force explicit declaration of all variables.</span></span> <span data-ttu-id="734f1-134">A tentativa de usar uma variável não declarada causa um erro no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="734f1-134">Attempting to use an undeclared variable causes an error at compile time.</span></span>  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a><span data-ttu-id="734f1-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="734f1-135">See also</span></span>

- [<span data-ttu-id="734f1-136">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="734f1-136">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="734f1-137">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="734f1-137">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="734f1-138">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="734f1-138">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="734f1-139">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="734f1-139">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="734f1-140">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="734f1-140">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="734f1-141">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="734f1-141">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="734f1-142">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="734f1-142">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="734f1-143">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="734f1-143">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
