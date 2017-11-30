---
title: /netcf
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a75573b0881af71e907a488c2b3c15db3816fc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="netcf"></a><span data-ttu-id="bd929-102">/netcf</span><span class="sxs-lookup"><span data-stu-id="bd929-102">/netcf</span></span>
<span data-ttu-id="bd929-103">Define o compilador como destino o [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd929-103">Sets the compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd929-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd929-104">Syntax</span></span>  
  
```  
/netcf  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd929-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd929-105">Remarks</span></span>  
 <span data-ttu-id="bd929-106">O `/netcf` opção faz com que o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador ao destino de [!INCLUDE[Compact](~/includes/compact-md.md)] em vez de toda [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd929-106">The `/netcf` option causes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to target the [!INCLUDE[Compact](~/includes/compact-md.md)] rather than the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="bd929-107">Funcionalidade de idioma que está presente somente no completa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="bd929-107">Language functionality that is present only in the full [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is disabled.</span></span>  
  
 <span data-ttu-id="bd929-108">O `/netcf` opção é projetada para ser usada com [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span><span class="sxs-lookup"><span data-stu-id="bd929-108">The `/netcf` option is designed to be used with [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md).</span></span> <span data-ttu-id="bd929-109">Os recursos de idioma desabilitados por `/netcf` são os mesmos recursos de idioma não está presentes nos arquivos de destino com `/sdkpath`.</span><span class="sxs-lookup"><span data-stu-id="bd929-109">The language features disabled by `/netcf` are the same language features not present in the files targeted with `/sdkpath`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd929-110">O `/netcf` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bd929-110">The `/netcf` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="bd929-111">O `/netcf` opção é definida quando um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dispositivo projeto é carregado.</span><span class="sxs-lookup"><span data-stu-id="bd929-111">The `/netcf` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="bd929-112">O `/netcf` opção altera os seguintes recursos de idioma:</span><span class="sxs-lookup"><span data-stu-id="bd929-112">The `/netcf` option changes the following language features:</span></span>  
  
-   <span data-ttu-id="bd929-113">O [final \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) palavra-chave que finaliza a execução de um programa, está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="bd929-113">The [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) keyword, which terminates execution of a program, is disabled.</span></span> <span data-ttu-id="bd929-114">O programa a seguir compila e executa sem `/netcf` , mas falhar no tempo de compilação com `/netcf`.</span><span class="sxs-lookup"><span data-stu-id="bd929-114">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   <span data-ttu-id="bd929-115">Associação tardia em todos os formulários, está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="bd929-115">Late binding, in all forms, is disabled.</span></span> <span data-ttu-id="bd929-116">Erros de tempo de compilação são gerados quando forem encontrados reconhecidos cenários de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="bd929-116">Compile-time errors are generated when recognized late-binding scenarios are encountered.</span></span> <span data-ttu-id="bd929-117">O programa a seguir compila e executa sem `/netcf` , mas falhar no tempo de compilação com `/netcf`.</span><span class="sxs-lookup"><span data-stu-id="bd929-117">The following program compiles and runs without `/netcf` but fails at compile time with `/netcf`.</span></span>  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   <span data-ttu-id="bd929-118">O [automática](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), e [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modificadores estão desabilitados.</span><span class="sxs-lookup"><span data-stu-id="bd929-118">The [Auto](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), and [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifiers are disabled.</span></span> <span data-ttu-id="bd929-119">A sintaxe do [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) instrução também é modificada para `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span><span class="sxs-lookup"><span data-stu-id="bd929-119">The syntax of the [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) statement is also modified to `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`.</span></span> <span data-ttu-id="bd929-120">O código a seguir mostra o efeito de `/netcf` em uma compilação.</span><span class="sxs-lookup"><span data-stu-id="bd929-120">The following code shows the effect of `/netcf` on a compilation.</span></span>  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   <span data-ttu-id="bd929-121">Usando o Visual Basic 6.0 palavras-chave que foram removidas da [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gera um erro diferente quando `/netcf` é usado.</span><span class="sxs-lookup"><span data-stu-id="bd929-121">Using Visual Basic 6.0 keywords that were removed from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generates a different error when `/netcf` is used.</span></span> <span data-ttu-id="bd929-122">Isso afeta as mensagens de erro para as seguintes palavras-chave:</span><span class="sxs-lookup"><span data-stu-id="bd929-122">This affects the error messages for the following keywords:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bd929-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd929-123">Example</span></span>  
 <span data-ttu-id="bd929-124">O código a seguir compila `Myfile.vb` com o [!INCLUDE[Compact](~/includes/compact-md.md)], usando as versões de mscorlib. dll e Microsoft.VisualBasic.dll encontrado no diretório de instalação padrão do [!INCLUDE[Compact](~/includes/compact-md.md)] na unidade C.</span><span class="sxs-lookup"><span data-stu-id="bd929-124">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="bd929-125">Normalmente, você poderia usar a versão mais recente do [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd929-125">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd929-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd929-126">See Also</span></span>  
 [<span data-ttu-id="bd929-127">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd929-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bd929-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd929-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="bd929-129">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="bd929-129">/sdkpath</span></span>](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
