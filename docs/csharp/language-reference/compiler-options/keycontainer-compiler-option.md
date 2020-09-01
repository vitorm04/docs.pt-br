---
description: -keycontainer (opções do compilador C#)
title: -keycontainer (opções do compilador C#)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 8b11380683159b7792149558a5dd432707ba3818
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125495"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="98555-103">-keycontainer (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="98555-103">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="98555-104">Especifica o nome do contêiner da chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="98555-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98555-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98555-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="98555-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="98555-106">Arguments</span></span>  
 `string`  
 <span data-ttu-id="98555-107">O nome do contêiner de chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="98555-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98555-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="98555-108">Remarks</span></span>  
 <span data-ttu-id="98555-109">Quando a opção **-keycontainer** for usada, o compilador criará um componente compartilhável.</span><span class="sxs-lookup"><span data-stu-id="98555-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="98555-110">O compilador insere uma chave pública do contêiner especificado no manifesto do assembly e assina o assembly final com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="98555-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="98555-111">Para gerar um arquivo de chave, digite `sn -k file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="98555-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="98555-112">`sn -i` instala o par de chaves no contêiner.</span><span class="sxs-lookup"><span data-stu-id="98555-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="98555-113">Não há suporte para essa opção quando o compilador é executado no CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="98555-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="98555-114">Para assinar um assembly ao compilar no CoreCLR, use a opção [-keyfile](keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="98555-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="98555-115">Se você compilar com [-target:module](./target-module-compiler-option.md), o nome do arquivo de chave será mantido no módulo e incorporado no assembly quando você compilar esse módulo em um assembly com [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="98555-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="98555-116">Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="98555-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="98555-117">Também é possível passar suas informações de criptografia para o compilador com [-keyfile](./keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="98555-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="98555-118">Use [-delaysign](./delaysign-compiler-option.md) se você quiser que a chave pública seja adicionada ao manifesto do assembly, mas deseja atrasar a assinatura do assembly até que ela seja testada.</span><span class="sxs-lookup"><span data-stu-id="98555-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="98555-119">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../standard/assembly/create-use-strong-named.md) e [Atraso na Assinatura de um Assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="98555-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="98555-120">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="98555-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="98555-121">Essa opção do compilador não está disponível no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98555-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="98555-122">Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="98555-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98555-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="98555-123">See also</span></span>

- [<span data-ttu-id="98555-124">Opção -keyfile do compilador C#</span><span class="sxs-lookup"><span data-stu-id="98555-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="98555-125">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="98555-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="98555-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="98555-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
