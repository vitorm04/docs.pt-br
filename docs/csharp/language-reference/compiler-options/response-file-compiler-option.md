---
description: '@ (Opções do compilador de C#)'
title: '@ (Opções do compilador de C#)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: 89a057cba6e0d23c15fc9b652e5bfbc89b6ecbaa
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128641"
---
# <a name="-c-compiler-options"></a><span data-ttu-id="9bc13-103">@ (Opções do compilador de C#)</span><span class="sxs-lookup"><span data-stu-id="9bc13-103">@ (C# Compiler Options)</span></span>
<span data-ttu-id="9bc13-104">A opção @ possibilita especificar um arquivo que contém opções do compilador e arquivos de código-fonte a serem compilados.</span><span class="sxs-lookup"><span data-stu-id="9bc13-104">The @ option lets you specify a file that contains compiler options and source code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc13-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bc13-105">Syntax</span></span>  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="9bc13-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9bc13-106">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="9bc13-107">Um arquivo que lista as opções do compilador ou os arquivos de código-fonte a serem compilados.</span><span class="sxs-lookup"><span data-stu-id="9bc13-107">A file that lists compiler options or source code files to compile.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bc13-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bc13-108">Remarks</span></span>  
 <span data-ttu-id="9bc13-109">As opções do compilador e os arquivos de código-fonte serão processados pelo compilador apenas se eles tiverem sido especificados na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9bc13-109">The compiler options and source code files will be processed by the compiler just as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="9bc13-110">Para especificar mais de um arquivo de resposta em uma compilação, especifique várias opções de arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="9bc13-110">To specify more than one response file in a compilation, specify multiple response file options.</span></span> <span data-ttu-id="9bc13-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9bc13-111">For example:</span></span>  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="9bc13-112">Em um arquivo de resposta, várias opções de compilador e de arquivos de código-fonte podem ser exibidas em uma linha.</span><span class="sxs-lookup"><span data-stu-id="9bc13-112">In a response file, multiple compiler options and source code files can appear on one line.</span></span> <span data-ttu-id="9bc13-113">Uma única especificação de opção do compilador deve ser exibida em uma linha (não é possível abranger várias linhas).</span><span class="sxs-lookup"><span data-stu-id="9bc13-113">A single compiler option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="9bc13-114">Os arquivos de resposta podem ter comentários que começam com o símbolo #.</span><span class="sxs-lookup"><span data-stu-id="9bc13-114">Response files can have comments that begin with the # symbol.</span></span>  
  
 <span data-ttu-id="9bc13-115">Especificar opções do compilador de dentro de um arquivo de resposta é como emitir esses comandos na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="9bc13-115">Specifying compiler options from within a response file is just like issuing those commands on the command line.</span></span> <span data-ttu-id="9bc13-116">Consulte [Compilando da linha de comando](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9bc13-116">See [Building from the Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md) for more information.</span></span>  
  
 <span data-ttu-id="9bc13-117">O compilador processa as opções de comando como elas são encontradas.</span><span class="sxs-lookup"><span data-stu-id="9bc13-117">The compiler processes the command options as they are encountered.</span></span> <span data-ttu-id="9bc13-118">Portanto, os argumentos da linha de comando podem substituir opções listadas anteriormente em arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="9bc13-118">Therefore, command line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="9bc13-119">Por outro lado, opções em um arquivo de resposta substituirão as opções listadas anteriormente na linha de comando ou em outros arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="9bc13-119">Conversely, options in a response file will override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="9bc13-120">O C# fornece o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe.</span><span class="sxs-lookup"><span data-stu-id="9bc13-120">C# provides the csc.rsp file, which is located in the same directory as the csc.exe file.</span></span> <span data-ttu-id="9bc13-121">Consulte [-noconfig](./noconfig-compiler-option.md) para obter mais informações sobre CSC. rsp.</span><span class="sxs-lookup"><span data-stu-id="9bc13-121">See [-noconfig](./noconfig-compiler-option.md) for more information on csc.rsp.</span></span>  
  
 <span data-ttu-id="9bc13-122">Essa opção do compilador não pode ser definida no ambiente de desenvolvimento do Visual Studio nem pode ser alterada por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="9bc13-122">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bc13-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bc13-123">Example</span></span>  
 <span data-ttu-id="9bc13-124">A seguir, há algumas linhas de um exemplo de arquivo de resposta:</span><span class="sxs-lookup"><span data-stu-id="9bc13-124">The following are a few lines from a sample response file:</span></span>  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bc13-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bc13-125">See also</span></span>

- [<span data-ttu-id="9bc13-126">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="9bc13-126">C# Compiler Options</span></span>](./index.md)
