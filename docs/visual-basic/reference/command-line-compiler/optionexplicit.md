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
ms.openlocfilehash: 65cc3fb1b2fa9daa04013caa2b93a3949d0a15b9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098929"
---
# <a name="-optionexplicit"></a><span data-ttu-id="13435-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="13435-102">-optionexplicit</span></span>

<span data-ttu-id="13435-103">Faz com que o compilador Relate erros se as variáveis não forem declaradas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="13435-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13435-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13435-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="13435-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="13435-105">Arguments</span></span>  

 <span data-ttu-id="13435-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="13435-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="13435-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="13435-107">Optional.</span></span> <span data-ttu-id="13435-108">Especifique `-optionexplicit+` para exigir declaração explícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="13435-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="13435-109">A `-optionexplicit+` opção é o padrão e é a mesma que `-optionexplicit` .</span><span class="sxs-lookup"><span data-stu-id="13435-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="13435-110">A `-optionexplicit-` opção habilita a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="13435-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13435-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="13435-111">Remarks</span></span>  

 <span data-ttu-id="13435-112">Se o arquivo de código-fonte contiver uma [instrução Option Explicit](../../language-reference/statements/option-explicit-statement.md), a instrução substituirá a `-optionexplicit` configuração do compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="13435-112">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="13435-113">Para Set-optionexplicit no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13435-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="13435-114">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="13435-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="13435-115">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="13435-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="13435-116">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="13435-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="13435-117">Modifique o valor na caixa **Option Explicit** .</span><span class="sxs-lookup"><span data-stu-id="13435-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13435-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13435-118">Example</span></span>  

 <span data-ttu-id="13435-119">O código a seguir é compilado quando `-optionexplicit-` é usado.</span><span class="sxs-lookup"><span data-stu-id="13435-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="13435-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="13435-120">See also</span></span>

- [<span data-ttu-id="13435-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13435-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="13435-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="13435-122">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="13435-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="13435-123">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="13435-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="13435-124">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="13435-125">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="13435-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="13435-126">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="13435-126">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="13435-127">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="13435-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
