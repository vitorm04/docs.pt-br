---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400547"
---
# <a name="-optioncompare"></a><span data-ttu-id="9bd42-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="9bd42-102">-optioncompare</span></span>

<span data-ttu-id="9bd42-103">Especifica como são feitas comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9bd42-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bd42-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd42-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="9bd42-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd42-105">Remarks</span></span>

<span data-ttu-id="9bd42-106">Você pode especificar `-optioncompare` em uma das duas formas: `-optioncompare:binary` para usar comparações de cadeia de caracteres binárias e para usar comparações de `-optioncompare:text` cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="9bd42-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="9bd42-107">Por padrão, o compilador usa o `-optioncompare:binary` .</span><span class="sxs-lookup"><span data-stu-id="9bd42-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="9bd42-108">No Microsoft Windows, a página de código atual determina a ordem de classificação binária.</span><span class="sxs-lookup"><span data-stu-id="9bd42-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="9bd42-109">Uma ordem de classificação binária típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="9bd42-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="9bd42-110">As comparações de cadeia de caracteres baseadas em texto são baseadas em uma ordem de classificação de texto que não diferencia maiúsculas de minúsculas determinada pela localidade do seu sistema.</span><span class="sxs-lookup"><span data-stu-id="9bd42-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="9bd42-111">Uma ordem de classificação de texto típica é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="9bd42-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="9bd42-112">Para Set-optioncompare no IDE do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9bd42-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="9bd42-113">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="9bd42-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9bd42-114">No menu **Projeto** , clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9bd42-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="9bd42-115">Clique na guia **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="9bd42-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="9bd42-116">Modifique o valor na caixa de **comparação de opções** .</span><span class="sxs-lookup"><span data-stu-id="9bd42-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="9bd42-117">Para Set-optioncompare programaticamente</span><span class="sxs-lookup"><span data-stu-id="9bd42-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="9bd42-118">Consulte a [instrução de comparação de opção](../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9bd42-118">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="9bd42-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd42-119">Example</span></span>

<span data-ttu-id="9bd42-120">O código a seguir compila `ProjFile.vb` e usa comparações de cadeia de caracteres binárias.</span><span class="sxs-lookup"><span data-stu-id="9bd42-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="9bd42-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bd42-121">See also</span></span>

- [<span data-ttu-id="9bd42-122">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bd42-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9bd42-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="9bd42-123">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="9bd42-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="9bd42-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="9bd42-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="9bd42-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="9bd42-126">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd42-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="9bd42-127">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="9bd42-127">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="9bd42-128">Caixa de diálogo Padrões do Visual Basic, Projetos, Opções</span><span class="sxs-lookup"><span data-stu-id="9bd42-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
