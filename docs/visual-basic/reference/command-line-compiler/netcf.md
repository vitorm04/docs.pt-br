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
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005451"
---
# <a name="-netcf"></a><span data-ttu-id="89163-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="89163-102">-netcf</span></span>

<span data-ttu-id="89163-103">Define o compilador para o .NET Compact Framework de destino.</span><span class="sxs-lookup"><span data-stu-id="89163-103">Sets the compiler to target the .NET Compact Framework.</span></span>

## <a name="syntax"></a><span data-ttu-id="89163-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89163-104">Syntax</span></span>

```console
-netcf
```

## <a name="remarks"></a><span data-ttu-id="89163-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="89163-105">Remarks</span></span>

<span data-ttu-id="89163-106">A opção `-netcf` faz com que o compilador Visual Basic direcione o .NET Compact Framework em vez do .NET Framework completo.</span><span class="sxs-lookup"><span data-stu-id="89163-106">The `-netcf` option causes the Visual Basic compiler to target the .NET Compact Framework rather than the full .NET Framework.</span></span> <span data-ttu-id="89163-107">A funcionalidade de idioma que está presente somente no .NET Framework completo está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="89163-107">Language functionality that is present only in the full .NET Framework is disabled.</span></span>

<span data-ttu-id="89163-108">A opção `-netcf` foi projetada para ser usada com [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="89163-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="89163-109">Os recursos de idioma desabilitados pelo `-netcf` são os mesmos recursos de linguagem que não estão presentes nos arquivos de destino com `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="89163-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>

> [!NOTE]
> <span data-ttu-id="89163-110">A opção `-netcf` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="89163-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="89163-111">A opção `-netcf` é definida quando um projeto de dispositivo Visual Basic é carregado.</span><span class="sxs-lookup"><span data-stu-id="89163-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>

<span data-ttu-id="89163-112">A opção `-netcf` altera os seguintes recursos de idioma:</span><span class="sxs-lookup"><span data-stu-id="89163-112">The `-netcf` option changes the following language features:</span></span>

- <span data-ttu-id="89163-113">A palavra-chave da [instrução > End \<keyword](../../../visual-basic/language-reference/statements/end-keyword-statement.md) , que encerra a execução de um programa, está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="89163-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="89163-114">O programa a seguir compila e executa sem `-netcf`, mas falha em tempo de compilação com `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="89163-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- <span data-ttu-id="89163-115">A associação tardia, em todos os formulários, está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="89163-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="89163-116">Erros de tempo de compilação são gerados quando cenários de ligação tardia reconhecidos são encontrados.</span><span class="sxs-lookup"><span data-stu-id="89163-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="89163-117">O programa a seguir compila e executa sem `-netcf`, mas falha em tempo de compilação com `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="89163-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- <span data-ttu-id="89163-118">Os modificadores [auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="89163-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="89163-119">A sintaxe da instrução de [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) também é modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="89163-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="89163-120">O código a seguir mostra o efeito de `-netcf` em uma compilação.</span><span class="sxs-lookup"><span data-stu-id="89163-120">The following code shows the effect of `-netcf` on a compilation.</span></span>

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- <span data-ttu-id="89163-121">Usar as palavras-chave Visual Basic 6,0 que foram removidas do Visual Basic gera um erro diferente quando `-netcf` é usado.</span><span class="sxs-lookup"><span data-stu-id="89163-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="89163-122">Isso afeta as mensagens de erro para as seguintes palavras-chave:</span><span class="sxs-lookup"><span data-stu-id="89163-122">This affects the error messages for the following keywords:</span></span>

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

## <a name="example"></a><span data-ttu-id="89163-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89163-123">Example</span></span>

<span data-ttu-id="89163-124">O código a seguir compila `Myfile.vb` com o .NET Compact Framework, usando as versões de mscorlib. dll e Microsoft. VisualBasic. dll encontrados no diretório de instalação padrão do .NET Compact Framework na unidade C.</span><span class="sxs-lookup"><span data-stu-id="89163-124">The following code compiles `Myfile.vb` with the .NET Compact Framework, using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the .NET Compact Framework on the C drive.</span></span> <span data-ttu-id="89163-125">Normalmente, você usaria a versão mais recente do .NET Compact Framework.</span><span class="sxs-lookup"><span data-stu-id="89163-125">Typically, you would use the most recent version of the .NET Compact Framework.</span></span>

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a><span data-ttu-id="89163-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89163-126">See also</span></span>

- [<span data-ttu-id="89163-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89163-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="89163-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="89163-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="89163-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="89163-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
