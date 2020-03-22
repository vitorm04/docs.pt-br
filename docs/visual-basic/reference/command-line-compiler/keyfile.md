---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266736"
---
# <a name="-keyfile"></a><span data-ttu-id="f76f0-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="f76f0-102">-keyfile</span></span>
<span data-ttu-id="f76f0-103">Especifica um arquivo contendo uma chave ou um par de tecla para dar a um conjunto um nome forte.</span><span class="sxs-lookup"><span data-stu-id="f76f0-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f76f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f76f0-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f76f0-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f76f0-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="f76f0-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="f76f0-106">Required.</span></span> <span data-ttu-id="f76f0-107">Arquivo que contém a chave.</span><span class="sxs-lookup"><span data-stu-id="f76f0-107">File that contains the key.</span></span> <span data-ttu-id="f76f0-108">Se o nome do arquivo contiver um espaço, feche o nome entre aspas (" ").</span><span class="sxs-lookup"><span data-stu-id="f76f0-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f76f0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f76f0-109">Remarks</span></span>  
 <span data-ttu-id="f76f0-110">O compilador insere a chave pública no manifesto de montagem e, em seguida, assina a montagem final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="f76f0-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="f76f0-111">Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f76f0-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="f76f0-112">Para obter mais informações, consulte [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="f76f0-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="f76f0-113">Se você compilar com `-target:module`, o nome do arquivo-chave é mantido no módulo e incorporado no conjunto que é criado quando você compila um conjunto com [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="f76f0-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="f76f0-114">Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="f76f0-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="f76f0-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="f76f0-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="f76f0-116">Você também pode especificar essa<xref:System.Reflection.AssemblyKeyFileAttribute>opção como um atributo personalizado ( ) no código-fonte de qualquer módulo de idioma intermediário da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f76f0-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="f76f0-117">No caso `-keyfile` de ambos e [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) serem especificados (seja por opção de linha de comando ou por atributo personalizado) na mesma compilação, o compilador primeiro tenta o contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="f76f0-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="f76f0-118">Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="f76f0-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="f76f0-119">Se o compilador não encontrar o recipiente de chave, `-keyfile`ele tentará o arquivo especificado com .</span><span class="sxs-lookup"><span data-stu-id="f76f0-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="f76f0-120">Se isso for bem sucedido, o conjunto é assinado com as informações no arquivo-chave, `sn -i`e as informações-chave são instaladas no recipiente de chave (semelhante a ) para que na próxima compilação, o recipiente de chave seja válido.</span><span class="sxs-lookup"><span data-stu-id="f76f0-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="f76f0-121">Observe que um arquivo de chave pode conter somente a chave pública.</span><span class="sxs-lookup"><span data-stu-id="f76f0-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="f76f0-122">Consulte [Criando e Usando Assembléias com Named Forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar uma assembléia.</span><span class="sxs-lookup"><span data-stu-id="f76f0-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f76f0-123">A `-keyfile` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele só está disponível quando compilado a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f76f0-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="f76f0-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f76f0-124">Example</span></span>

<span data-ttu-id="f76f0-125">O código a seguir `Input.vb` compila o arquivo fonte e especifica um arquivo-chave.</span><span class="sxs-lookup"><span data-stu-id="f76f0-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="f76f0-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="f76f0-126">See also</span></span>

- [<span data-ttu-id="f76f0-127">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="f76f0-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="f76f0-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f76f0-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f76f0-129">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f76f0-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="f76f0-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="f76f0-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
