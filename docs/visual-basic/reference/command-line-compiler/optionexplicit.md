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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005309"
---
# <a name="-optionexplicit"></a><span data-ttu-id="3b28e-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3b28e-102">-optionexplicit</span></span>
<span data-ttu-id="3b28e-103">Faz com que o compilador Relate erros se as variáveis não forem declaradas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="3b28e-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b28e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b28e-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b28e-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3b28e-105">Arguments</span></span>  
 <span data-ttu-id="3b28e-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="3b28e-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="3b28e-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3b28e-107">Optional.</span></span> <span data-ttu-id="3b28e-108">Especifique `-optionexplicit+` para exigir declaração explícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="3b28e-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="3b28e-109">A opção `-optionexplicit+` é o padrão e é a mesma que `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="3b28e-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="3b28e-110">A opção `-optionexplicit-` habilita a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="3b28e-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b28e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b28e-111">Remarks</span></span>  
 <span data-ttu-id="3b28e-112">Se o arquivo de código-fonte contiver uma [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substituirá a configuração do compilador de linha de comando `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="3b28e-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="3b28e-113">Para Set-optionexplicit no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b28e-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="3b28e-114">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="3b28e-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3b28e-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3b28e-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="3b28e-116">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="3b28e-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="3b28e-117">Modifique o valor na caixa **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="3b28e-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b28e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b28e-118">Example</span></span>  
 <span data-ttu-id="3b28e-119">O código a seguir é compilado quando `-optionexplicit-` é usado.</span><span class="sxs-lookup"><span data-stu-id="3b28e-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3b28e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b28e-120">See also</span></span>

- [<span data-ttu-id="3b28e-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b28e-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3b28e-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3b28e-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="3b28e-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="3b28e-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="3b28e-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="3b28e-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="3b28e-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b28e-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="3b28e-126">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="3b28e-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="3b28e-127">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="3b28e-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
