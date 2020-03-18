---
title: '@ (Opções do compilador de C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: d8e5c0ec148754c3e4cebfa32ad9f44a0bb0119e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70202912"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="493f2-102">@ (Opções do compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="493f2-102">@ (C# Compiler Options)</span></span>
<span data-ttu-id="493f2-103">A opção @ possibilita especificar um arquivo que contém opções do compilador e arquivos de código-fonte a serem compilados.</span><span class="sxs-lookup"><span data-stu-id="493f2-103">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="493f2-104">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="493f2-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="493f2-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="493f2-106">Um arquivo que lista as opções do compilador ou os arquivos de código-fonte a serem compilados.</span><span class="sxs-lookup"><span data-stu-id="493f2-106">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="493f2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="493f2-107">Remarks</span></span>  
 <span data-ttu-id="493f2-108">As opções do compilador e os arquivos de código-fonte serão processados pelo compilador apenas se eles tiverem sido especificados na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="493f2-108">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="493f2-109">Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="493f2-109">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="493f2-110">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="493f2-110">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="493f2-111">Em um arquivo de resposta, várias opções de compilador e de arquivos de código-fonte podem ser exibidas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="493f2-111">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="493f2-112">Uma única especificação de opção do compilador deve ser exibida em uma linha (não é possível abranger várias linhas).</span><span class="sxs-lookup"><span data-stu-id="493f2-112">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="493f2-113">Os arquivos de resposta podem ter comentários que começam com o símbolo #.</span><span class="sxs-lookup"><span data-stu-id="493f2-113">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="493f2-114">Especificar opções do compilador de dentro de um arquivo de resposta é como emitir esses comandos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="493f2-114">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="493f2-115">Consulte [Compilando da linha de comando](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="493f2-115">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="493f2-116">O compilador processa as opções de comando como elas são encontradas.</span><span class="sxs-lookup"><span data-stu-id="493f2-116">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="493f2-117">Portanto, os argumentos da linha de comando podem substituir opções listadas anteriormente em arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="493f2-117">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="493f2-118">Por outro lado, opções em um arquivo de resposta substituirão as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="493f2-118">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="493f2-119">O C# fornece o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe.</span><span class="sxs-lookup"><span data-stu-id="493f2-119">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="493f2-120">Consulte [-noconfig](./noconfig-compiler-option.md) para obter mais informações sobre csc.rsp.</span><span class="sxs-lookup"><span data-stu-id="493f2-120">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="493f2-121">Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="493f2-121">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="493f2-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="493f2-122">Example</span></span>  
 <span data-ttu-id="493f2-123">A seguir, há algumas linhas de um exemplo de arquivo de resposta:</span><span class="sxs-lookup"><span data-stu-id="493f2-123">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="493f2-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="493f2-124">See also</span></span>

- [<span data-ttu-id="493f2-125">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="493f2-125">C# Compiler Options</span></span>](./index.md)
