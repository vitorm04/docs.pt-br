---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="943cf-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="943cf-102">/optionexplicit</span></span>
<span data-ttu-id="943cf-103">Faz com que o compilador para relatar erros se variáveis não são declaradas antes de serem usadas.</span><span class="sxs-lookup"><span data-stu-id="943cf-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="943cf-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="943cf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="943cf-105">Arguments</span></span>  
 <span data-ttu-id="943cf-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="943cf-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="943cf-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="943cf-107">Optional.</span></span> <span data-ttu-id="943cf-108">Especifique `/optionexplicit+` para requer declaração explícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="943cf-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="943cf-109">O `/optionexplicit+` opção é o padrão e é o mesmo que `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="943cf-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="943cf-110">O `/optionexplicit-` opção permite que a declaração implícita de variáveis.</span><span class="sxs-lookup"><span data-stu-id="943cf-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943cf-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="943cf-111">Remarks</span></span>  
 <span data-ttu-id="943cf-112">Se o arquivo de código fonte contém um [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substitui a `/optionexplicit` configuração do compilador de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="943cf-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="943cf-113">Para definir /optionexplicit no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="943cf-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="943cf-114">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="943cf-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="943cf-115">No menu **Projeto**, clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="943cf-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="943cf-116">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="943cf-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="943cf-117">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="943cf-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="943cf-118">Modificar o valor de **Option Explicit** caixa.</span><span class="sxs-lookup"><span data-stu-id="943cf-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="943cf-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="943cf-119">Example</span></span>  
 <span data-ttu-id="943cf-120">O código a seguir compila quando `/optionexplicit-` é usado.</span><span class="sxs-lookup"><span data-stu-id="943cf-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="943cf-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="943cf-121">See Also</span></span>  
 [<span data-ttu-id="943cf-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="943cf-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="943cf-123">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="943cf-123">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="943cf-124">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="943cf-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="943cf-125">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="943cf-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="943cf-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="943cf-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="943cf-127">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="943cf-127">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="943cf-128">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="943cf-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
