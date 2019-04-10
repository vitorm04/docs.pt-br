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
ms.openlocfilehash: e18fe451ea4a80ac959ed61b66394920f8bf177f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336077"
---
# <a name="-optionstrict"></a><span data-ttu-id="8e376-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="8e376-102">-optionstrict</span></span>
<span data-ttu-id="8e376-103">Impõe semântica de tipo estrito para restringir conversões de tipo implícito.</span><span class="sxs-lookup"><span data-stu-id="8e376-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e376-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e376-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e376-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8e376-105">Arguments</span></span>  
 `+` <span data-ttu-id="8e376-106">&#124;</span><span class="sxs-lookup"><span data-stu-id="8e376-106">&#124;</span></span> `-`  
 <span data-ttu-id="8e376-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8e376-107">Optional.</span></span> <span data-ttu-id="8e376-108">O `-optionstrict+` opção restringe a conversão implícita de tipo.</span><span class="sxs-lookup"><span data-stu-id="8e376-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="8e376-109">O padrão para essa opção é `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="8e376-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="8e376-110">O `-optionstrict+` opção é o mesmo que `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="8e376-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="8e376-111">Você pode usar ambos para a semântica de tipo permissível.</span><span class="sxs-lookup"><span data-stu-id="8e376-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="8e376-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8e376-112">Required.</span></span> <span data-ttu-id="8e376-113">Avise quando a semântica de linguagem estrita não for respeitada.</span><span class="sxs-lookup"><span data-stu-id="8e376-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e376-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e376-114">Remarks</span></span>  
 <span data-ttu-id="8e376-115">Quando `-optionstrict+` é na verdade, apenas conversões de tipo de expansão podem ser feitas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="8e376-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="8e376-116">Implícita reduzir conversões de tipo, como a atribuição de um `Decimal` tipo de objeto a um objeto de tipo inteiro, são relatados como erros.</span><span class="sxs-lookup"><span data-stu-id="8e376-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="8e376-117">Para gerar avisos para conversões de tipo de estreitamento implícitas, use `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="8e376-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="8e376-118">Use `-nowarn:numberlist` para ignorar os avisos específicos e `-warnaserror:numberlist` para tratar específicos avisos como erros.</span><span class="sxs-lookup"><span data-stu-id="8e376-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="8e376-119">Definir - optionstrict no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8e376-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="8e376-120">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="8e376-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8e376-121">Sobre o **Project** menu, clique em **propriedades.**</span><span class="sxs-lookup"><span data-stu-id="8e376-121">On the **Project** menu, click **Properties.**</span></span>   
  
2. <span data-ttu-id="8e376-122">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="8e376-122">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="8e376-123">Modificar o valor de **Option Strict** caixa.</span><span class="sxs-lookup"><span data-stu-id="8e376-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="8e376-124">Definir - optionstrict programaticamente</span><span class="sxs-lookup"><span data-stu-id="8e376-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="8e376-125">Ver [opção Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8e376-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e376-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e376-126">Example</span></span>  
 <span data-ttu-id="8e376-127">O seguinte código compila `Test.vb` usando a semântica de tipo estrito.</span><span class="sxs-lookup"><span data-stu-id="8e376-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e376-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e376-128">See also</span></span>

- [<span data-ttu-id="8e376-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e376-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8e376-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="8e376-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="8e376-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="8e376-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="8e376-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="8e376-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="8e376-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="8e376-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="8e376-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e376-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="8e376-135">Linhas de comando de compilação de exemplo</span><span class="sxs-lookup"><span data-stu-id="8e376-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="8e376-136">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="8e376-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="8e376-137">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="8e376-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
