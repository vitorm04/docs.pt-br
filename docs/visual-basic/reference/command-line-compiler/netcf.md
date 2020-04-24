---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 7f14ce07a2928f4dbffd3aa57f8cdd514b75694c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716710"
---
# <a name="-netcf"></a><span data-ttu-id="51d96-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="51d96-102">-netcf</span></span>

<span data-ttu-id="51d96-103">Define o compilador para o .NET Compact Framework de destino.</span><span class="sxs-lookup"><span data-stu-id="51d96-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="51d96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51d96-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="51d96-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="51d96-105">Remarks</span></span>

<span data-ttu-id="51d96-106">A `-netcf` opção faz com que o compilador de Visual Basic direcione o .NET Compact Framework em vez do .NET Framework completo.</span><span class="sxs-lookup"><span data-stu-id="51d96-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="51d96-107">A funcionalidade de idioma que está presente somente no .NET Framework completo está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="51d96-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="51d96-108">A `-netcf` opção foi projetada para ser usada com [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="51d96-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="51d96-109">Os recursos de idioma desabilitados pelo `-netcf` são os mesmos recursos de linguagem que não estão presentes `-sdkpath`nos arquivos de destino com o.</span><span class="sxs-lookup"><span data-stu-id="51d96-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="51d96-110">A `-netcf` opção não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="51d96-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="51d96-111">A `-netcf` opção é definida quando um projeto de dispositivo Visual Basic é carregado.</span><span class="sxs-lookup"><span data-stu-id="51d96-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="51d96-112">A `-netcf` opção altera os seguintes recursos de idioma:</span><span class="sxs-lookup"><span data-stu-id="51d96-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="51d96-113">A [palavra \<-chave end keyword>](../../../visual-basic/language-reference/statements/end-keyword-statement.md) palavra-chave Statement, que encerra a execução de um programa, está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="51d96-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="51d96-114">O programa a seguir compila e executa sem `-netcf` , mas falha no momento da compilação `-netcf`com.</span><span class="sxs-lookup"><span data-stu-id="51d96-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="51d96-115">A associação tardia, em todos os formulários, está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="51d96-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="51d96-116">Erros de tempo de compilação são gerados quando cenários de ligação tardia reconhecidos são encontrados.</span><span class="sxs-lookup"><span data-stu-id="51d96-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="51d96-117">O programa a seguir compila e executa sem `-netcf` , mas falha no momento da compilação `-netcf`com.</span><span class="sxs-lookup"><span data-stu-id="51d96-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="51d96-118">Os modificadores [auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="51d96-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="51d96-119">A sintaxe da [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) também é modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="51d96-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="51d96-120">O código a seguir mostra o efeito `-netcf` de em uma compilação.</span><span class="sxs-lookup"><span data-stu-id="51d96-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="51d96-121">Usar as palavras-chave Visual Basic 6,0 que foram removidas do Visual Basic gera um `-netcf` erro diferente quando é usado.</span><span class="sxs-lookup"><span data-stu-id="51d96-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="51d96-122">Isso afeta as mensagens de erro para as seguintes palavras-chave:</span><span class="sxs-lookup"><span data-stu-id="51d96-122">This affects the error messages for the following keywords:</span></span>

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a><span data-ttu-id="51d96-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51d96-123">Example</span></span>

<span data-ttu-id="51d96-124">O código a seguir é compilado `Myfile.vb` com o .NET Compact Framework, usando as versões de mscorlib. dll e Microsoft. VisualBasic. dll encontrados no diretório de instalação padrão do .NET Compact Framework na unidade C.</span><span class="sxs-lookup"><span data-stu-id="51d96-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="51d96-125">Normalmente, você usaria a versão mais recente do .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="51d96-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="51d96-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="51d96-126">See also</span></span>

- [<span data-ttu-id="51d96-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51d96-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="51d96-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="51d96-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="51d96-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="51d96-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
