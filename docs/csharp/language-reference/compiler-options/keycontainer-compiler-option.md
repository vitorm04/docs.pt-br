---
title: -keycontainer (opções do compilador C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: cf51bccc98f04c38149ec821b7064a4844d7e804
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302771"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="d5ff4-102">-keycontainer (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d5ff4-102">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="d5ff4-103">Especifica o nome do contêiner da chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5ff4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5ff4-104">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5ff4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d5ff4-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="d5ff4-106">O nome do contêiner de chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5ff4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5ff4-107">Remarks</span></span>  
 <span data-ttu-id="d5ff4-108">Quando a opção **-keycontainer** for usada, o compilador criará um componente compartilhável.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-108">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="d5ff4-109">O compilador insere uma chave pública do contêiner especificado no manifesto do assembly e assina o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-109">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="d5ff4-110">Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-110">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="d5ff4-111">`sn -i` instala o par de chaves no contêiner.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-111">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="d5ff4-112">Não há suporte para essa opção quando o compilador é executado no CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-112">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="d5ff4-113">Para assinar um assembly ao compilar no CoreCLR, use a opção [-keyfile](keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d5ff4-113">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="d5ff4-114">Se você compilar com [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), o nome do arquivo de chave será mantido no módulo e incorporado no assembly quando você compilar esse módulo em um assembly com [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d5ff4-114">If you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="d5ff4-115">Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="d5ff4-115">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="d5ff4-116">Também é possível passar suas informações de criptografia para o compilador com [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d5ff4-116">You can also pass your encryption information to the compiler with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="d5ff4-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se você quiser que a chave pública seja adicionada ao manifesto do assembly, mas deseja atrasar a assinatura do assembly até que ela seja testada.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-117">Use [-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="d5ff4-118">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d5ff4-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d5ff4-119">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5ff4-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d5ff4-120">Essa opção do compilador não está disponível no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-120">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="d5ff4-121">Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5ff4-121">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ff4-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5ff4-122">See also</span></span>

- [<span data-ttu-id="d5ff4-123">Opção -keyfile do compilador C#</span><span class="sxs-lookup"><span data-stu-id="d5ff4-123">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="d5ff4-124">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="d5ff4-124">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="d5ff4-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="d5ff4-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
