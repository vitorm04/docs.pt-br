---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: da1bd6d3b6746561655a82cd49aa0014563a1d40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-optionstrict"></a><span data-ttu-id="fc24a-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="fc24a-102">-optionstrict</span></span>
<span data-ttu-id="fc24a-103">Impõe a semântica de tipo estrito para restringir a conversões de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="fc24a-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc24a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc24a-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc24a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc24a-105">Arguments</span></span>  
 <span data-ttu-id="fc24a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="fc24a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="fc24a-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="fc24a-107">Optional.</span></span> <span data-ttu-id="fc24a-108">O `-optionstrict+` opção restringe a conversão implícita de tipo.</span><span class="sxs-lookup"><span data-stu-id="fc24a-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="fc24a-109">O padrão para essa opção é `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="fc24a-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="fc24a-110">O `-optionstrict+` opção é o mesmo que `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="fc24a-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="fc24a-111">Você pode usar para a semântica de tipo permissivo.</span><span class="sxs-lookup"><span data-stu-id="fc24a-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="fc24a-112">Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="fc24a-112">Required.</span></span> <span data-ttu-id="fc24a-113">Avise quando a semântica de linguagem estrita não for respeitada.</span><span class="sxs-lookup"><span data-stu-id="fc24a-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc24a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc24a-114">Remarks</span></span>  
 <span data-ttu-id="fc24a-115">Quando `-optionstrict+` está em vigor, conversões de tipo de expansão somente pode ser feito implicitamente.</span><span class="sxs-lookup"><span data-stu-id="fc24a-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="fc24a-116">Implícita de conversões de tipo, como a atribuição entre um `Decimal` tipo de objeto para um objeto de tipo inteiro, são relatados como erros.</span><span class="sxs-lookup"><span data-stu-id="fc24a-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="fc24a-117">Para gerar avisos para conversões de tipo de restrição implícita, use `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="fc24a-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="fc24a-118">Use `-nowarn:numberlist` para ignorar os avisos específicos e `-warnaserror:numberlist` para tratar específicos avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="fc24a-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="fc24a-119">Para definir - optionstrict no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc24a-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="fc24a-120">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="fc24a-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fc24a-121">Sobre o **projeto** menu, clique em **propriedades.**</span><span class="sxs-lookup"><span data-stu-id="fc24a-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="fc24a-122">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="fc24a-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="fc24a-123">Modificar o valor de **Option Strict** caixa.</span><span class="sxs-lookup"><span data-stu-id="fc24a-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="fc24a-124">Definir - optionstrict programaticamente</span><span class="sxs-lookup"><span data-stu-id="fc24a-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="fc24a-125">Consulte [opção Strict instrução](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fc24a-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc24a-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc24a-126">Example</span></span>  
 <span data-ttu-id="fc24a-127">O código a seguir compila `Test.vb` usando semântica de tipo estrito.</span><span class="sxs-lookup"><span data-stu-id="fc24a-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc24a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc24a-128">See Also</span></span>  
 [<span data-ttu-id="fc24a-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc24a-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fc24a-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="fc24a-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="fc24a-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="fc24a-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="fc24a-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="fc24a-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="fc24a-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="fc24a-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="fc24a-134">-/warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc24a-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="fc24a-135">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc24a-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="fc24a-136">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="fc24a-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="fc24a-137">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="fc24a-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
