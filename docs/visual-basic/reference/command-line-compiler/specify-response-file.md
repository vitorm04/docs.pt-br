---
title: '@ (especificar arquivo de resposta) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4201dcc094364899984e13c85f2f43a6467ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653618"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="222c4-102">@ (especificar arquivo de resposta) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="222c4-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="222c4-103">Especifica um arquivo que contém opções do compilador e arquivos de código-fonte para compilar.</span><span class="sxs-lookup"><span data-stu-id="222c4-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="222c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="222c4-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="222c4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="222c4-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="222c4-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="222c4-106">Required.</span></span> <span data-ttu-id="222c4-107">Um arquivo que lista as opções do compilador ou arquivos de código-fonte para compilar.</span><span class="sxs-lookup"><span data-stu-id="222c4-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="222c4-108">Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="222c4-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="222c4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="222c4-109">Remarks</span></span>  
 <span data-ttu-id="222c4-110">O compilador processa as opções do compilador e arquivos de código-fonte especificados em um arquivo de resposta como se eles tivessem sido especificados na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="222c4-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="222c4-111">Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta, como a seguir.</span><span class="sxs-lookup"><span data-stu-id="222c4-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="222c4-112">Arquivo, várias opções do compilador e arquivos de código-fonte podem aparecer em uma linha em uma resposta.</span><span class="sxs-lookup"><span data-stu-id="222c4-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="222c4-113">Uma especificação de opção de compilador único deve aparecer em uma linha (não pode abranger várias linhas).</span><span class="sxs-lookup"><span data-stu-id="222c4-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="222c4-114">Arquivos de resposta podem ter os comentários que começam com o `#` símbolo.</span><span class="sxs-lookup"><span data-stu-id="222c4-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="222c4-115">Você pode combinar as opções especificadas na linha de comando com as opções especificadas em um ou mais arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="222c4-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="222c4-116">O compilador processa as opções de comando como encontrá-las.</span><span class="sxs-lookup"><span data-stu-id="222c4-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="222c4-117">Portanto, argumentos de linha de comando podem substituir as opções listadas anteriormente em arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="222c4-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="222c4-118">Por outro lado, opções em um arquivo de resposta substituem as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="222c4-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="222c4-119">Visual Basic fornece o arquivo Vbc.rsp, que está localizado no mesmo diretório que o arquivo Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="222c4-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="222c4-120">O arquivo Vbc.rsp está incluído por padrão, a menos que o `-noconfig` opção é usada.</span><span class="sxs-lookup"><span data-stu-id="222c4-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="222c4-121">Para obter mais informações, consulte [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="222c4-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="222c4-122">O `@` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="222c4-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="222c4-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="222c4-123">Example</span></span>  
 <span data-ttu-id="222c4-124">As linhas a seguir são de um arquivo de resposta de exemplo.</span><span class="sxs-lookup"><span data-stu-id="222c4-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="222c4-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="222c4-125">Example</span></span>  
 <span data-ttu-id="222c4-126">O exemplo a seguir demonstra como usar o `@` opção com o arquivo de resposta chamado `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="222c4-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="222c4-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="222c4-127">See Also</span></span>  
 [<span data-ttu-id="222c4-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="222c4-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="222c4-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="222c4-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="222c4-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="222c4-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
