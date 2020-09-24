---
description: -keyfile (opções do compilador C#)
title: -keyfile (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 5af40da18895d47933cb809d710e31a40f14513b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152423"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="81618-103">-keyfile (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="81618-103">-keyfile (C# Compiler Options)</span></span>

<span data-ttu-id="81618-104">Especifica o nome de arquivo que contém a chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="81618-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81618-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81618-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="81618-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="81618-106">Arguments</span></span>  
  
|<span data-ttu-id="81618-107">Termo</span><span class="sxs-lookup"><span data-stu-id="81618-107">Term</span></span>|<span data-ttu-id="81618-108">Definição</span><span class="sxs-lookup"><span data-stu-id="81618-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="81618-109">O nome do arquivo que contém a chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="81618-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81618-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="81618-110">Remarks</span></span>  

 <span data-ttu-id="81618-111">Quando esta opção é usada, o compilador insere a chave pública da linha especificada no manifesto do assembly e, em seguida, assina o assembly definitivo com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="81618-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="81618-112">Para gerar um arquivo de chave, digite sn -k `file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="81618-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="81618-113">Se você compilar com **-target:module**, o nome do arquivo de chave será mantido no módulo e incorporado no assembly, criado quando você compila um assembly com [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="81618-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="81618-114">Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="81618-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="81618-115">Use [-delaysign](./delaysign-compiler-option.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="81618-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="81618-116">Caso -keyfile e -keycontainer sejam especificados (pela opção de linha de comando ou pelo atributo personalizado) na mesma compilação, o compilador tentará primeiro o contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="81618-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="81618-117">Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="81618-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="81618-118">Se o compilador não localizar o contêiner de chaves, ele tentará o arquivo especificado com -keyfile.</span><span class="sxs-lookup"><span data-stu-id="81618-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="81618-119">Se isso ocorrer, o assembly será assinado com as informações no arquivo de chave e as informações da chave serão instaladas no contêiner de chaves (semelhante a sn -i), de forma que, na próxima compilação, o contêiner de chaves será válido.</span><span class="sxs-lookup"><span data-stu-id="81618-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="81618-120">Observe que um arquivo de chave pode conter somente a chave pública.</span><span class="sxs-lookup"><span data-stu-id="81618-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="81618-121">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../standard/assembly/create-use-strong-named.md) e [Atraso na Assinatura de um Assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="81618-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="81618-122">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="81618-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="81618-123">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="81618-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="81618-124">Clique na página de propriedades **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="81618-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="81618-125">Modifique a propriedade **Escolha um arquivo de chave de nome forte**.</span><span class="sxs-lookup"><span data-stu-id="81618-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="81618-126">Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="81618-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81618-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="81618-127">See also</span></span>

- [<span data-ttu-id="81618-128">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="81618-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="81618-129">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="81618-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
