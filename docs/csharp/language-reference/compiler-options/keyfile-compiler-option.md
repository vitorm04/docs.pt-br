---
title: -keyfile (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 45ab88609c26dd26a1f8bb3d68d1f579af9d3f77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214007"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="5450b-102">-keyfile (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="5450b-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="5450b-103">Especifica o nome de arquivo que contém a chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="5450b-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5450b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5450b-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5450b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5450b-105">Arguments</span></span>  
  
|<span data-ttu-id="5450b-106">Termo</span><span class="sxs-lookup"><span data-stu-id="5450b-106">Term</span></span>|<span data-ttu-id="5450b-107">Definição</span><span class="sxs-lookup"><span data-stu-id="5450b-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="5450b-108">O nome do arquivo que contém a chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="5450b-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5450b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5450b-109">Remarks</span></span>  
 <span data-ttu-id="5450b-110">Quando esta opção é usada, o compilador insere a chave pública da linha especificada no manifesto do assembly e, em seguida, assina o assembly definitivo com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="5450b-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="5450b-111">Para gerar um arquivo de chave, digite sn -k `file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5450b-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="5450b-112">Se você compilar com **-target:module**, o nome do arquivo de chave será mantido no módulo e incorporado no assembly, criado quando você compila um assembly com [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5450b-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="5450b-113">Também é possível passar suas informações de criptografia para o compilador com [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5450b-113">You can also pass your encryption information to the compiler with [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span> <span data-ttu-id="5450b-114">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se quiser um assembly parcialmente assinado.</span><span class="sxs-lookup"><span data-stu-id="5450b-114">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="5450b-115">Caso -keyfile e -keycontainer sejam especificados (pela opção de linha de comando ou pelo atributo personalizado) na mesma compilação, o compilador tentará primeiro o contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="5450b-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="5450b-116">Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="5450b-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="5450b-117">Se o compilador não localizar o contêiner de chaves, ele tentará o arquivo especificado com -keyfile.</span><span class="sxs-lookup"><span data-stu-id="5450b-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="5450b-118">Se isso ocorrer, o assembly será assinado com as informações no arquivo de chave e as informações da chave serão instaladas no contêiner de chaves (semelhante a sn -i), de forma que, na próxima compilação, o contêiner de chaves será válido.</span><span class="sxs-lookup"><span data-stu-id="5450b-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="5450b-119">Observe que um arquivo de chave pode conter somente a chave pública.</span><span class="sxs-lookup"><span data-stu-id="5450b-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="5450b-120">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="5450b-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5450b-121">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5450b-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="5450b-122">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="5450b-122">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="5450b-123">Clique na página de propriedades **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="5450b-123">Click the **Signing** property page.</span></span>  
  
3.  <span data-ttu-id="5450b-124">Modifique a propriedade **Escolha um arquivo de chave de nome forte**.</span><span class="sxs-lookup"><span data-stu-id="5450b-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="5450b-125">Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="5450b-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5450b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5450b-126">See Also</span></span>  
 [<span data-ttu-id="5450b-127">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="5450b-127">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="5450b-128">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="5450b-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
