---
title: /optionstrict | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
dev_langs:
- VB
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
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
ms.openlocfilehash: c22445cb53ca4f5621cf7aa69ab840b26f8e08c9
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="optionstrict"></a><span data-ttu-id="a0b81-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="a0b81-102">/optionstrict</span></span>
<span data-ttu-id="a0b81-103">Impõe semântica de tipo estrito para restringir a conversões de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="a0b81-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0b81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0b81-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0b81-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a0b81-105">Arguments</span></span>  
 <span data-ttu-id="a0b81-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a0b81-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a0b81-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a0b81-107">Optional.</span></span> <span data-ttu-id="a0b81-108">O `/optionstrict+` opção restringe a conversão implícita de tipo.</span><span class="sxs-lookup"><span data-stu-id="a0b81-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="a0b81-109">O padrão para essa opção é `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="a0b81-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="a0b81-110">O `/optionstrict+` opção é o mesmo que `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="a0b81-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="a0b81-111">Você pode usar para a semântica de tipo permissivas.</span><span class="sxs-lookup"><span data-stu-id="a0b81-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="a0b81-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a0b81-112">Required.</span></span> <span data-ttu-id="a0b81-113">Avisar quando a semântica de linguagem estrita não for respeitada.</span><span class="sxs-lookup"><span data-stu-id="a0b81-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0b81-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0b81-114">Remarks</span></span>  
 <span data-ttu-id="a0b81-115">Quando `/optionstrict+` estiver em efeito, apenas conversões de tipo alargamento podem ser feito implicitamente.</span><span class="sxs-lookup"><span data-stu-id="a0b81-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="a0b81-116">Implícita reduzir conversões de tipo, como a atribuição de um `Decimal` tipo de objeto para um objeto de tipo inteiro, são relatados como erros.</span><span class="sxs-lookup"><span data-stu-id="a0b81-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="a0b81-117">Para gerar avisos de conversões implícitas de tipo restrição, use `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="a0b81-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="a0b81-118">Use `/nowarn:numberlist` para ignorar os avisos específicos e `/warnaserror:numberlist` para tratar específicos avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="a0b81-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="a0b81-119">Definir /optionstrict no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a0b81-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="a0b81-120">Tenha um projeto selecionado no **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="a0b81-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a0b81-121">Sobre o **projeto** menu, clique em **propriedades.**</span><span class="sxs-lookup"><span data-stu-id="a0b81-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="a0b81-122">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="a0b81-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="a0b81-123">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="a0b81-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="a0b81-124">Modificar o valor de **Option Strict** caixa.</span><span class="sxs-lookup"><span data-stu-id="a0b81-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="a0b81-125">Definir /optionstrict programaticamente</span><span class="sxs-lookup"><span data-stu-id="a0b81-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="a0b81-126">Consulte [opção Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a0b81-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0b81-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0b81-127">Example</span></span>  
 <span data-ttu-id="a0b81-128">O seguinte código compila `Test.vb` usando a semântica de tipo estrito.</span><span class="sxs-lookup"><span data-stu-id="a0b81-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0b81-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0b81-129">See Also</span></span>  
 <span data-ttu-id="a0b81-130">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-130">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="a0b81-131"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-131"> [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) </span></span>  
<span data-ttu-id="a0b81-132"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-132"> [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) </span></span>  
<span data-ttu-id="a0b81-133"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-133"> [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) </span></span>  
<span data-ttu-id="a0b81-134"> [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-134"> [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) </span></span>  
<span data-ttu-id="a0b81-135"> [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-135"> [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md) </span></span>  
<span data-ttu-id="a0b81-136"> [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-136"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="a0b81-137"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a0b81-137"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="a0b81-138"> [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="a0b81-138"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
