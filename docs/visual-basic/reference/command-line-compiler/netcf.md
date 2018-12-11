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
ms.openlocfilehash: d213f0f95d047a3758a4c85e4dc8263f82dcac8a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130201"
---
# <a name="-netcf"></a><span data-ttu-id="6d32e-102">-netcf</span><span class="sxs-lookup"><span data-stu-id="6d32e-102">-netcf</span></span>
<span data-ttu-id="6d32e-103">Define o compilador como destino o [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d32e-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d32e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d32e-104">Syntax</span></span>  
  
```  
-netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="6d32e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d32e-105">Remarks</span></span>  
 <span data-ttu-id="6d32e-106">O `-netcf` opção faz com que o compilador do Visual Basic para o destino do [!INCLUDE[Compact](~/includes/compact-md.md)] em vez de todo o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d32e-106">The `-netcf` option causes the Visual Basic compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="6d32e-107">Funcionalidades de linguagem que estão presentes apenas em todo o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="6d32e-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="6d32e-108">O `-netcf` opção é projetada para ser usada com [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="6d32e-108">The `-netcf` option is designed to be used with [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="6d32e-109">Os recursos de linguagem desabilitados por `-netcf` são os mesmos recursos de idioma não está presentes nos arquivos de destino com `-sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="6d32e-109">The language features disabled by `-netcf` are the same language features not present in the files targeted with `-sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d32e-110">O `-netcf` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="6d32e-110">The `-netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="6d32e-111">O `-netcf` opção é definida quando um projeto de dispositivo do Visual Basic é carregado.</span><span class="sxs-lookup"><span data-stu-id="6d32e-111">The `-netcf` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="6d32e-112">O `-netcf` opção altera os seguintes recursos de idioma:</span><span class="sxs-lookup"><span data-stu-id="6d32e-112">The `-netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="6d32e-113">O [final \<palavra-chave > demonstrativo](../../../visual-basic/language-reference/statements/end-keyword-statement.md) palavra-chave, que finaliza a execução de um programa, está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="6d32e-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="6d32e-114">O programa a seguir compila e executa sem `-netcf` , mas falhar no tempo de compilação com `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="6d32e-114">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="6d32e-115">Associação tardia em todos os formulários, está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="6d32e-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="6d32e-116">Erros de tempo de compilação são gerados quando os cenários de associação tardia reconhecidos são encontrados.</span><span class="sxs-lookup"><span data-stu-id="6d32e-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="6d32e-117">O programa a seguir compila e executa sem `-netcf` , mas falhar no tempo de compilação com `-netcf`.</span><span class="sxs-lookup"><span data-stu-id="6d32e-117">The following program compiles and runs without `-netcf` but fails at compile time with `-netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="6d32e-118">O [automática](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificadores estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="6d32e-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="6d32e-119">A sintaxe do [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrução também será modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="6d32e-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="6d32e-120">O código a seguir mostra o efeito de `-netcf` em uma compilação.</span><span class="sxs-lookup"><span data-stu-id="6d32e-120">The following code shows the effect of `-netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="6d32e-121">Usando o Visual Basic 6.0 as palavras-chave que foram removidas do Visual Basic gera um erro diferente quando `-netcf` é usado.</span><span class="sxs-lookup"><span data-stu-id="6d32e-121">Using Visual Basic 6.0 keywords that were removed from Visual Basic generates a different error when `-netcf` is used.</span></span> <span data-ttu-id="6d32e-122">Isso afeta as mensagens de erro para as seguintes palavras-chave:</span><span class="sxs-lookup"><span data-stu-id="6d32e-122">This affects the error messages for the following keywords:</span></span>  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a><span data-ttu-id="6d32e-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d32e-123">Example</span></span>  
 <span data-ttu-id="6d32e-124">O seguinte código compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e VisualBasic encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C.</span><span class="sxs-lookup"><span data-stu-id="6d32e-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="6d32e-125">Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d32e-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d32e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d32e-126">See Also</span></span>  
 [<span data-ttu-id="6d32e-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d32e-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="6d32e-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d32e-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="6d32e-129">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="6d32e-129">-sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
