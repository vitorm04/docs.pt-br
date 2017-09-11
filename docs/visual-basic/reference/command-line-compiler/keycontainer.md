---
title: /keycontainer | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a783ef85e6ff2b7c6f889f809291ca8c275e709a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="keycontainer"></a><span data-ttu-id="51c6f-102">/keycontainer</span><span class="sxs-lookup"><span data-stu-id="51c6f-102">/keycontainer</span></span>
<span data-ttu-id="51c6f-103">Especifica um nome de contêiner de chave para um par de chaves dar um nome forte de um assembly.</span><span class="sxs-lookup"><span data-stu-id="51c6f-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c6f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51c6f-104">Syntax</span></span>  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="51c6f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="51c6f-105">Arguments</span></span>  
  
|<span data-ttu-id="51c6f-106">Termo</span><span class="sxs-lookup"><span data-stu-id="51c6f-106">Term</span></span>|<span data-ttu-id="51c6f-107">Definição</span><span class="sxs-lookup"><span data-stu-id="51c6f-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="51c6f-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="51c6f-108">Required.</span></span> <span data-ttu-id="51c6f-109">Arquivo de contêiner que contém a chave.</span><span class="sxs-lookup"><span data-stu-id="51c6f-109">Container file that contains the key.</span></span> <span data-ttu-id="51c6f-110">Coloque o nome do arquivo entre aspas ("") se o nome contém um espaço.</span><span class="sxs-lookup"><span data-stu-id="51c6f-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51c6f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="51c6f-111">Remarks</span></span>  
 <span data-ttu-id="51c6f-112">O compilador cria o componente compartilhável inserindo uma chave pública no manifesto do assembly e assinando o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="51c6f-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="51c6f-113">Para gerar um arquivo de chave, digite `sn -k``file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="51c6f-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="51c6f-114">O `-i` opção instala o par de chaves no contêiner.</span><span class="sxs-lookup"><span data-stu-id="51c6f-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="51c6f-115">Para saber mais, veja [Sn.exe (Ferramenta de Nome Forte)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="51c6f-115">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="51c6f-116">Se você compilar com `/target:module`, o nome do arquivo da chave é mantido no módulo e incorporado no assembly, que é criado quando você compila um assembly com [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="51c6f-116">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="51c6f-117">Você também pode especificar esta opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute>) no código-fonte para qualquer módulo do Microsoft intermediate language (MSIL).</xref:System.Reflection.AssemblyKeyNameAttribute></span><span class="sxs-lookup"><span data-stu-id="51c6f-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="51c6f-118">Você também pode passar suas informações de criptografia para o compilador com [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="51c6f-118">You can also pass your encryption information to the compiler with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="51c6f-119">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se você quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="51c6f-119">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="51c6f-120">Consulte [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="51c6f-120">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51c6f-121">O `/keycontainer` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="51c6f-121">The `/keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51c6f-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51c6f-122">Example</span></span>  
 <span data-ttu-id="51c6f-123">O código a seguir compila o arquivo de origem `Input.vb` e especifica um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="51c6f-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="51c6f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51c6f-124">See Also</span></span>  
 <span data-ttu-id="51c6f-125">[Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="51c6f-125">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="51c6f-126"> [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="51c6f-126"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="51c6f-127"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="51c6f-127"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="51c6f-128"> [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="51c6f-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
