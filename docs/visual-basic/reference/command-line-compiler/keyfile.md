---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c81486243195f7d022bd474ef6db20d069b3a018
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085146"
---
# <a name="-keyfile"></a><span data-ttu-id="fcc44-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="fcc44-102">-keyfile</span></span>

<span data-ttu-id="fcc44-103">Especifica um arquivo que contém uma chave ou um par de chaves para fornecer um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="fcc44-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fcc44-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fcc44-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="fcc44-105">Arguments</span></span>  

 `file`  
 <span data-ttu-id="fcc44-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fcc44-106">Required.</span></span> <span data-ttu-id="fcc44-107">Arquivo que contém a chave.</span><span class="sxs-lookup"><span data-stu-id="fcc44-107">File that contains the key.</span></span> <span data-ttu-id="fcc44-108">Se o nome do arquivo contiver um espaço, coloque o nome entre aspas ("").</span><span class="sxs-lookup"><span data-stu-id="fcc44-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcc44-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fcc44-109">Remarks</span></span>  

 <span data-ttu-id="fcc44-110">O compilador insere a chave pública no manifesto do assembly e, em seguida, assina o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="fcc44-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="fcc44-111">Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fcc44-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="fcc44-112">Para obter mais informações, consulte [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="fcc44-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="fcc44-113">Se você compilar with `-target:module` , o nome do arquivo de chave será mantido no módulo e incorporado ao assembly criado quando você compilar um assembly com o [módulo-](addmodule.md)Add.</span><span class="sxs-lookup"><span data-stu-id="fcc44-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="fcc44-114">Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="fcc44-114">You can also pass your encryption information to the compiler with [-keycontainer](keycontainer.md).</span></span> <span data-ttu-id="fcc44-115">Use [-delaysign](delaysign.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="fcc44-115">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="fcc44-116">Você também pode especificar essa opção como um atributo personalizado ( <xref:System.Reflection.AssemblyKeyFileAttribute> ) no código-fonte para qualquer módulo de linguagem intermediária da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fcc44-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="fcc44-117">Caso both `-keyfile` e [-keycontainer](keycontainer.md) sejam especificados (por opção de linha de comando ou por atributo personalizado) na mesma compilação, o compilador primeiro tenta o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="fcc44-117">In case both `-keyfile` and [-keycontainer](keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="fcc44-118">Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="fcc44-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="fcc44-119">Se o compilador não encontrar o contêiner de chave, ele tentará o arquivo especificado com `-keyfile` .</span><span class="sxs-lookup"><span data-stu-id="fcc44-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="fcc44-120">Se isso for bem sucedido, o assembly será assinado com as informações no arquivo de chave e as informações de chave serão instaladas no contêiner de chave (semelhante a `sn -i` ) para que, na próxima compilação, o contêiner de chave seja válido.</span><span class="sxs-lookup"><span data-stu-id="fcc44-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="fcc44-121">Observe que um arquivo de chave pode conter somente a chave pública.</span><span class="sxs-lookup"><span data-stu-id="fcc44-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="fcc44-122">Consulte [criando e usando assemblies de nome forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="fcc44-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcc44-123">A `-keyfile` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fcc44-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="fcc44-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcc44-124">Example</span></span>

<span data-ttu-id="fcc44-125">O código a seguir compila o arquivo `Input.vb` de origem e especifica um arquivo de chave.</span><span class="sxs-lookup"><span data-stu-id="fcc44-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="fcc44-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="fcc44-126">See also</span></span>

- [<span data-ttu-id="fcc44-127">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="fcc44-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="fcc44-128">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcc44-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="fcc44-129">-referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcc44-129">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="fcc44-130">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcc44-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
