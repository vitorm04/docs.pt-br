---
title: '@ (especificar arquivo de resposta) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: deab111cc669941a1cd7dc143dd699b6521221bb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004984"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="3433d-102">@ (especificar arquivo de resposta) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3433d-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="3433d-103">Especifica um arquivo que contém opções de compilador e arquivos de código-fonte a serem compilados.</span><span class="sxs-lookup"><span data-stu-id="3433d-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3433d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3433d-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="3433d-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3433d-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="3433d-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3433d-106">Required.</span></span> <span data-ttu-id="3433d-107">Um arquivo que lista opções de compilador ou arquivos de código-fonte para compilar.</span><span class="sxs-lookup"><span data-stu-id="3433d-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="3433d-108">Coloque o nome de arquivo entre aspas ("") se ele contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="3433d-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3433d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3433d-109">Remarks</span></span>  
 <span data-ttu-id="3433d-110">O compilador processa as opções do compilador e os arquivos de código-fonte especificados em um arquivo de resposta como se eles tivessem sido especificados na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3433d-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="3433d-111">Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta, como a seguir.</span><span class="sxs-lookup"><span data-stu-id="3433d-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="3433d-112">Em um arquivo de resposta, várias opções de compilador e arquivos de código-fonte podem aparecer em uma linha.</span><span class="sxs-lookup"><span data-stu-id="3433d-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="3433d-113">Uma especificação de opção de compilador único deve aparecer em uma linha (não pode abranger várias linhas).</span><span class="sxs-lookup"><span data-stu-id="3433d-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="3433d-114">Os arquivos de resposta podem ter comentários que começam com o símbolo `#`.</span><span class="sxs-lookup"><span data-stu-id="3433d-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="3433d-115">Você pode combinar as opções especificadas na linha de comando com opções especificadas em um ou mais arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="3433d-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="3433d-116">O compilador processa as opções de comando à medida que as encontra.</span><span class="sxs-lookup"><span data-stu-id="3433d-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="3433d-117">Portanto, argumentos de linha de comando podem substituir as opções listadas anteriormente em arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="3433d-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="3433d-118">Por outro lado, as opções em um arquivo de resposta substituem as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="3433d-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="3433d-119">Visual Basic fornece o arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc. exe.</span><span class="sxs-lookup"><span data-stu-id="3433d-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="3433d-120">O arquivo Vbc. rsp é incluído por padrão, a menos que a opção `-noconfig` seja usada.</span><span class="sxs-lookup"><span data-stu-id="3433d-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="3433d-121">Para obter mais informações, consulte [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="3433d-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3433d-122">A opção `@` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="3433d-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3433d-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3433d-123">Example</span></span>  
 <span data-ttu-id="3433d-124">As linhas a seguir são de um exemplo de arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="3433d-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="3433d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3433d-125">Example</span></span>  
 <span data-ttu-id="3433d-126">O exemplo a seguir demonstra como usar a opção `@` com o arquivo de resposta chamado `File1.rsp`.</span><span class="sxs-lookup"><span data-stu-id="3433d-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="3433d-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3433d-127">See also</span></span>

- [<span data-ttu-id="3433d-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3433d-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="3433d-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="3433d-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="3433d-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="3433d-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
