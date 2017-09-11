---
title: "-keycontainer (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
dev_langs:
- CSharp
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5d27fa0b80ca6df15394ad1fda149377cac41a8b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="keycontainer-c-compiler-options"></a><span data-ttu-id="2295d-102">/keycontainer (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="2295d-102">/keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="2295d-103">Especifica o nome do contêiner da chave de criptografia.</span><span class="sxs-lookup"><span data-stu-id="2295d-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2295d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2295d-104">Syntax</span></span>  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="2295d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2295d-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="2295d-106">O nome do contêiner de chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="2295d-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2295d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2295d-107">Remarks</span></span>  
 <span data-ttu-id="2295d-108">Quando a opção **/keycontainer** é usada, o compilador cria um componente compartilhável inserindo uma chave pública do contêiner especificado no manifesto do assembly e assinando o assembly definitivo com a chave privada.</span><span class="sxs-lookup"><span data-stu-id="2295d-108">When the **/keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="2295d-109">Para gerar um arquivo de chave, digite sn -k `file` na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="2295d-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="2295d-110">O sn -i instala o par de chaves no contêiner.</span><span class="sxs-lookup"><span data-stu-id="2295d-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="2295d-111">Se você compilar com [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), o nome do arquivo de chave será mantido no módulo e incorporado no assembly quando você compilar esse módulo em um assembly com [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2295d-111">If you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="2295d-112">Também é possível especificar essa opção como um atributo personalizado (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) no código-fonte de qualquer módulo MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="2295d-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="2295d-113">Também é possível passar suas informações de criptografia para o compilador com [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="2295d-113">You can also pass your encryption information to the compiler with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="2295d-114">Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se você quiser a chave pública adicionada ao manifesto do assembly, mas deseja atrasar a assinatura do assembly até que ela seja testada.</span><span class="sxs-lookup"><span data-stu-id="2295d-114">Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="2295d-115">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](https://msdn.microsoft.com/library/xwb8f617) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="2295d-115">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2295d-116">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2295d-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="2295d-117">Essa opção do compilador não está disponível no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2295d-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="2295d-118">Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span><span class="sxs-lookup"><span data-stu-id="2295d-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2295d-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2295d-119">See Also</span></span>  
 <span data-ttu-id="2295d-120">[Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="2295d-120">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="2295d-121">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="2295d-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

