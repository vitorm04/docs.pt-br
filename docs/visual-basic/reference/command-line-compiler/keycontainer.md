---
title: -keycontainer
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b433182a502761fb3840ed2003cc50e053fb072a
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-keycontainer"></a><span data-ttu-id="bd8a0-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="bd8a0-102">-keycontainer</span></span>
<span data-ttu-id="bd8a0-103">Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd8a0-104">Syntax</span></span>  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd8a0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd8a0-105">Arguments</span></span>  
  
|<span data-ttu-id="bd8a0-106">Termo</span><span class="sxs-lookup"><span data-stu-id="bd8a0-106">Term</span></span>|<span data-ttu-id="bd8a0-107">Definição</span><span class="sxs-lookup"><span data-stu-id="bd8a0-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="bd8a0-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-108">Required.</span></span> <span data-ttu-id="bd8a0-109">Arquivo de contêiner que contém a chave.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-109">Container file that contains the key.</span></span> <span data-ttu-id="bd8a0-110">Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd8a0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd8a0-111">Remarks</span></span>  
 <span data-ttu-id="bd8a0-112">O compilador cria o componente compartilhável inserindo uma chave pública no manifesto do assembly e assinando o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="bd8a0-113">Para gerar um arquivo de chave, digite `sn -k``file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="bd8a0-114">O `-i` opção instala o par de chaves no contêiner.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="bd8a0-115">Para obter mais informações, consulte [Sn.exe (ferramenta de nome forte)][Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="bd8a0-115">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="bd8a0-116">Se você compilar com `-target:module`, o nome do arquivo da chave é mantido no módulo e incorporado no assembly, que é criado quando você compila um assembly com [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="bd8a0-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="bd8a0-117">Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="bd8a0-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="bd8a0-118">Também é possível passar suas informações de criptografia para o compilador com [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="bd8a0-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="bd8a0-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="bd8a0-120">Consulte [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-120">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd8a0-121">O `-keycontainer` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd8a0-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd8a0-122">Example</span></span>  
 <span data-ttu-id="bd8a0-123">O código a seguir compila o arquivo de origem `Input.vb` e especifica um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="bd8a0-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd8a0-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd8a0-124">See Also</span></span>  
 [<span data-ttu-id="bd8a0-125">Assemblies e o Cache de Assembly Global</span><span class="sxs-lookup"><span data-stu-id="bd8a0-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="bd8a0-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd8a0-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bd8a0-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="bd8a0-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="bd8a0-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd8a0-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
