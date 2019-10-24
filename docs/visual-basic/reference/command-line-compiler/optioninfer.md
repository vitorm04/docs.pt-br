---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d7209e431b84e52e487bccbf73bd633a346efde0
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775616"
---
# <a name="-optioninfer"></a><span data-ttu-id="98f01-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="98f01-102">-optioninfer</span></span>
<span data-ttu-id="98f01-103">Permite o uso de inferência de tipo local nas declarações de variáveis.</span><span class="sxs-lookup"><span data-stu-id="98f01-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98f01-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="98f01-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="98f01-105">Arguments</span></span>  
  
|<span data-ttu-id="98f01-106">Termo</span><span class="sxs-lookup"><span data-stu-id="98f01-106">Term</span></span>|<span data-ttu-id="98f01-107">Definição</span><span class="sxs-lookup"><span data-stu-id="98f01-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="98f01-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="98f01-108">`+` &#124; `-`</span></span>|<span data-ttu-id="98f01-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="98f01-109">Optional.</span></span> <span data-ttu-id="98f01-110">Especifique `-optioninfer+` para habilitar a inferência de tipo de local ou `-optioninfer-` para bloqueá-la.</span><span class="sxs-lookup"><span data-stu-id="98f01-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="98f01-111">A opção `-optioninfer`, sem valor especificado, é a mesma de `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="98f01-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="98f01-112">O valor padrão quando o comutador `-optioninfer` não estiver presente também é `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="98f01-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="98f01-113">O valor padrão é definido no arquivo de resposta Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="98f01-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="98f01-114">Você pode usar a opção `-noconfig` para manter os padrões internos do compilador em vez dos especificados no vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="98f01-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="98f01-115">O padrão do compilador para essa opção é `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="98f01-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98f01-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="98f01-116">Remarks</span></span>  
 <span data-ttu-id="98f01-117">Se o arquivo de código-fonte contiver uma [instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md), a instrução substituirá a configuração `-optioninfer` compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="98f01-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="98f01-118">Para Set-optioninfer no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98f01-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="98f01-119">Selecione um projeto no **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="98f01-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="98f01-120">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="98f01-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="98f01-121">Na guia **Compilar** , modifique o valor na caixa **Opção Infer** .</span><span class="sxs-lookup"><span data-stu-id="98f01-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98f01-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98f01-122">Example</span></span>  
 <span data-ttu-id="98f01-123">O seguinte código compila `test.vb` com a inferência de tipo local habilitada.</span><span class="sxs-lookup"><span data-stu-id="98f01-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="98f01-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98f01-124">See also</span></span>

- [<span data-ttu-id="98f01-125">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98f01-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="98f01-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="98f01-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="98f01-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="98f01-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="98f01-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="98f01-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="98f01-129">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="98f01-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="98f01-130">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="98f01-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="98f01-131">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="98f01-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="98f01-132">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="98f01-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="98f01-133">Página de Compilação, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98f01-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="98f01-134">-noconfig</span><span class="sxs-lookup"><span data-stu-id="98f01-134">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="98f01-135">Compilando da Linha de Comando</span><span class="sxs-lookup"><span data-stu-id="98f01-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
