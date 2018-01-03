---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 692681b21c243432ec8e7160bcc1eaa4e718d64d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="ec649-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="ec649-102">/optionstrict</span></span>
<span data-ttu-id="ec649-103">Impõe a semântica de tipo estrito para restringir a conversões de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="ec649-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec649-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec649-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec649-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ec649-105">Arguments</span></span>  
 <span data-ttu-id="ec649-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ec649-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ec649-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ec649-107">Optional.</span></span> <span data-ttu-id="ec649-108">O `/optionstrict+` opção restringe a conversão implícita de tipo.</span><span class="sxs-lookup"><span data-stu-id="ec649-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="ec649-109">O padrão para essa opção é `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="ec649-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="ec649-110">O `/optionstrict+` opção é o mesmo que `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="ec649-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="ec649-111">Você pode usar para a semântica de tipo permissivo.</span><span class="sxs-lookup"><span data-stu-id="ec649-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="ec649-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ec649-112">Required.</span></span> <span data-ttu-id="ec649-113">Avise quando a semântica de linguagem estrita não for respeitada.</span><span class="sxs-lookup"><span data-stu-id="ec649-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec649-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="ec649-114">Remarks</span></span>  
 <span data-ttu-id="ec649-115">Quando `/optionstrict+` está em vigor, conversões de tipo de expansão somente pode ser feito implicitamente.</span><span class="sxs-lookup"><span data-stu-id="ec649-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="ec649-116">Implícita de conversões de tipo, como a atribuição entre um `Decimal` tipo de objeto para um objeto de tipo inteiro, são relatados como erros.</span><span class="sxs-lookup"><span data-stu-id="ec649-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="ec649-117">Para gerar avisos para conversões de tipo de restrição implícita, use `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="ec649-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="ec649-118">Use `/nowarn:numberlist` para ignorar os avisos específicos e `/warnaserror:numberlist` para tratar específicos avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="ec649-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="ec649-119">Para definir /optionstrict no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec649-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="ec649-120">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="ec649-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ec649-121">Sobre o **projeto** menu, clique em **propriedades.**</span><span class="sxs-lookup"><span data-stu-id="ec649-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="ec649-122">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="ec649-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="ec649-123">Modificar o valor de **Option Strict** caixa.</span><span class="sxs-lookup"><span data-stu-id="ec649-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="ec649-124">Definir /optionstrict programaticamente</span><span class="sxs-lookup"><span data-stu-id="ec649-124">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="ec649-125">Consulte [opção Strict instrução](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ec649-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec649-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec649-126">Example</span></span>  
 <span data-ttu-id="ec649-127">O código a seguir compila `Test.vb` usando semântica de tipo estrito.</span><span class="sxs-lookup"><span data-stu-id="ec649-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec649-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec649-128">See Also</span></span>  
 [<span data-ttu-id="ec649-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ec649-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ec649-130">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="ec649-130">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="ec649-131">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="ec649-131">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="ec649-132">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="ec649-132">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="ec649-133">/nowarn</span><span class="sxs-lookup"><span data-stu-id="ec649-133">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="ec649-134">/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec649-134">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="ec649-135">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec649-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="ec649-136">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="ec649-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="ec649-137">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="ec649-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
