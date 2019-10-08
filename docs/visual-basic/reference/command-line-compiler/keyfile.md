---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: b17df3cb803cfbef324b74a9dee4394fce70215b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005548"
---
# <a name="-keyfile"></a><span data-ttu-id="275a3-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="275a3-102">-keyfile</span></span>
<span data-ttu-id="275a3-103">Especifica um arquivo que contém uma chave ou um par de chaves para fornecer um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="275a3-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="275a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="275a3-104">Syntax</span></span>  
  
```console 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="275a3-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="275a3-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="275a3-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="275a3-106">Required.</span></span> <span data-ttu-id="275a3-107">Arquivo que contém a chave.</span><span class="sxs-lookup"><span data-stu-id="275a3-107">File that contains the key.</span></span> <span data-ttu-id="275a3-108">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="275a3-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="275a3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="275a3-109">Remarks</span></span>  
 <span data-ttu-id="275a3-110">O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="275a3-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="275a3-111">Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="275a3-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="275a3-112">Para obter mais informações, consulte [sn. exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="275a3-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="275a3-113">Se você compilar com `-target:module`, o nome do arquivo de chave será mantido no módulo e incorporado ao assembly que é criado quando você compila um assembly com [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="275a3-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="275a3-114">Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="275a3-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="275a3-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="275a3-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="275a3-116">Você também pode especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyFileAttribute>) no código-fonte para qualquer módulo de linguagem intermediária da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="275a3-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="275a3-117">Caso ambos os `-keyfile` e [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) sejam especificados (por opção de linha de comando ou por atributo personalizado) na mesma compilação, o compilador primeiro tenta o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="275a3-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="275a3-118">Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="275a3-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="275a3-119">Se o compilador não encontrar o contêiner de chave, ele tentará o arquivo especificado com `-keyfile`.</span><span class="sxs-lookup"><span data-stu-id="275a3-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="275a3-120">Se isso for bem sucedido, o assembly será assinado com as informações no arquivo de chave e as informações de chave serão instaladas no contêiner de chave (semelhante a `sn -i`) para que, na próxima compilação, o contêiner de chave seja válido.</span><span class="sxs-lookup"><span data-stu-id="275a3-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="275a3-121">Observe que um arquivo de chave pode conter somente a chave pública.</span><span class="sxs-lookup"><span data-stu-id="275a3-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="275a3-122">Consulte [criando e usando assemblies de nome forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="275a3-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="275a3-123">A opção `-keyfile` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="275a3-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="275a3-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="275a3-124">Example</span></span>  
 <span data-ttu-id="275a3-125">O código a seguir compila o arquivo de origem `Input.vb` e especifica um arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="275a3-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="275a3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="275a3-126">See also</span></span>

- [<span data-ttu-id="275a3-127">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="275a3-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="275a3-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="275a3-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="275a3-129">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="275a3-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="275a3-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="275a3-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
