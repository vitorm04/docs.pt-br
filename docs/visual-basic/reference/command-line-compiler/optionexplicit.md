---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266723"
---
# <a name="-optionexplicit"></a><span data-ttu-id="86ef6-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="86ef6-102">-optionexplicit</span></span>
<span data-ttu-id="86ef6-103">Faz com que o compilador Relate erros se as variáveis não forem declaradas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="86ef6-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ef6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86ef6-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="86ef6-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="86ef6-105">Arguments</span></span>  
 <span data-ttu-id="86ef6-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="86ef6-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="86ef6-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="86ef6-107">Optional.</span></span> <span data-ttu-id="86ef6-108">Especifique `-optionexplicit+` para exigir declaração explícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="86ef6-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="86ef6-109">A `-optionexplicit+` opção é o padrão e é a mesma que `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="86ef6-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="86ef6-110">A `-optionexplicit-` opção habilita a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="86ef6-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86ef6-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="86ef6-111">Remarks</span></span>  
 <span data-ttu-id="86ef6-112">Se o arquivo de código-fonte contiver uma [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a `-optionexplicit` instrução substituirá a configuração do compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="86ef6-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="86ef6-113">Para Set-optionexplicit no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86ef6-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="86ef6-114">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="86ef6-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="86ef6-115">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="86ef6-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="86ef6-116">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="86ef6-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="86ef6-117">Modifique o valor na caixa **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="86ef6-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86ef6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86ef6-118">Example</span></span>  
 <span data-ttu-id="86ef6-119">O código a seguir é compilado quando `-optionexplicit-` é usado.</span><span class="sxs-lookup"><span data-stu-id="86ef6-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="86ef6-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="86ef6-120">See also</span></span>

- [<span data-ttu-id="86ef6-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86ef6-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="86ef6-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="86ef6-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="86ef6-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="86ef6-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="86ef6-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="86ef6-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="86ef6-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="86ef6-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="86ef6-126">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="86ef6-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="86ef6-127">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="86ef6-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
