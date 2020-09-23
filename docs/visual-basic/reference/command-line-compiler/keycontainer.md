---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 243583e55dcf278f951b813cca8384246d2d6db9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085224"
---
# <a name="-keycontainer"></a><span data-ttu-id="94608-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="94608-102">-keycontainer</span></span>

<span data-ttu-id="94608-103">Especifica um nome de contêiner de chave para um par de chaves para dar a um assembly um nome forte.</span><span class="sxs-lookup"><span data-stu-id="94608-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94608-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94608-104">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="94608-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="94608-105">Arguments</span></span>  
  
|<span data-ttu-id="94608-106">Termo</span><span class="sxs-lookup"><span data-stu-id="94608-106">Term</span></span>|<span data-ttu-id="94608-107">Definição</span><span class="sxs-lookup"><span data-stu-id="94608-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="94608-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94608-108">Required.</span></span> <span data-ttu-id="94608-109">Arquivo de contêiner que contém a chave.</span><span class="sxs-lookup"><span data-stu-id="94608-109">Container file that contains the key.</span></span> <span data-ttu-id="94608-110">Coloque o nome do arquivo entre aspas ("") se o nome contiver um espaço.</span><span class="sxs-lookup"><span data-stu-id="94608-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94608-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="94608-111">Remarks</span></span>  

 <span data-ttu-id="94608-112">O compilador cria o componente compartilhável inserindo uma chave pública no manifesto do assembly e assinando o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="94608-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="94608-113">Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="94608-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="94608-114">A `-i` opção instala o par de chaves em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="94608-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="94608-115">Para obter mais informações, consulte [Sn.exe (ferramenta de nome forte)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="94608-115">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="94608-116">Se você compilar with `-target:module` , o nome do arquivo de chave será mantido no módulo e incorporado ao assembly criado quando você compilar um assembly com o [módulo-](addmodule.md)Add.</span><span class="sxs-lookup"><span data-stu-id="94608-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="94608-117">Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="94608-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="94608-118">Também é possível passar suas informações de criptografia para o compilador com [-keyfile](keyfile.md).</span><span class="sxs-lookup"><span data-stu-id="94608-118">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="94608-119">Use [-delaysign](delaysign.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="94608-119">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="94608-120">Consulte [criando e usando assemblies de nome forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar um assembly.</span><span class="sxs-lookup"><span data-stu-id="94608-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94608-121">A `-keycontainer` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="94608-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94608-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94608-122">Example</span></span>  

 <span data-ttu-id="94608-123">O código a seguir compila o arquivo `Input.vb` de origem e especifica um contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="94608-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="94608-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="94608-124">See also</span></span>

- [<span data-ttu-id="94608-125">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="94608-125">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="94608-126">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="94608-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="94608-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="94608-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="94608-128">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="94608-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
