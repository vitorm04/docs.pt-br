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
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583082"
---
# <a name="-optionstrict"></a><span data-ttu-id="2e693-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="2e693-102">-optionstrict</span></span>

<span data-ttu-id="2e693-103">Impõe uma semântica de tipo estrito para restringir conversões implícitas de tipo.</span><span class="sxs-lookup"><span data-stu-id="2e693-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e693-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e693-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="2e693-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="2e693-105">Arguments</span></span>

<span data-ttu-id="2e693-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2e693-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="2e693-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2e693-107">Optional.</span></span> <span data-ttu-id="2e693-108">A `-optionstrict+` opção restringe a conversão implícita de tipo.</span><span class="sxs-lookup"><span data-stu-id="2e693-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="2e693-109">O padrão para essa opção é `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="2e693-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="2e693-110">A `-optionstrict+` opção é a mesma que `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="2e693-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="2e693-111">Você pode usar ambas as semânticas de tipo permissivas.</span><span class="sxs-lookup"><span data-stu-id="2e693-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="2e693-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="2e693-112">Required.</span></span> <span data-ttu-id="2e693-113">Avisar quando a semântica de linguagem estrita não for respeitada.</span><span class="sxs-lookup"><span data-stu-id="2e693-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e693-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e693-114">Remarks</span></span>

<span data-ttu-id="2e693-115">Quando `-optionstrict+` está em vigor, apenas as conversões de tipo de ampliação podem ser feitas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="2e693-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="2e693-116">As conversões de tipo de estreitamento implícita, como a atribuição de `Decimal` um objeto de tipo a um objeto de tipo inteiro, são relatadas como erros.</span><span class="sxs-lookup"><span data-stu-id="2e693-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="2e693-117">Para gerar avisos para conversões de tipo de estreitamento implícita, `-optionstrict:custom`use.</span><span class="sxs-lookup"><span data-stu-id="2e693-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="2e693-118">Use `-nowarn:numberlist` para ignorar avisos específicos e `-warnaserror:numberlist` tratar avisos específicos como erros.</span><span class="sxs-lookup"><span data-stu-id="2e693-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="2e693-119">Para Set-optionstrict no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2e693-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="2e693-120">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="2e693-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2e693-121">No menu **projeto** , clique em **Propriedades.**</span><span class="sxs-lookup"><span data-stu-id="2e693-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="2e693-122">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="2e693-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="2e693-123">Modifique o valor na caixa **Option Strict** .</span><span class="sxs-lookup"><span data-stu-id="2e693-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="2e693-124">Para Set-optionstrict programaticamente</span><span class="sxs-lookup"><span data-stu-id="2e693-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="2e693-125">Consulte a [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2e693-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e693-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e693-126">Example</span></span>

<span data-ttu-id="2e693-127">O código a seguir compila `Test.vb` usando semântica de tipo estrito.</span><span class="sxs-lookup"><span data-stu-id="2e693-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="2e693-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="2e693-128">See also</span></span>

- [<span data-ttu-id="2e693-129">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e693-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2e693-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="2e693-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="2e693-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="2e693-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="2e693-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="2e693-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="2e693-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="2e693-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="2e693-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e693-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="2e693-135">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="2e693-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="2e693-136">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="2e693-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="2e693-137">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="2e693-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
