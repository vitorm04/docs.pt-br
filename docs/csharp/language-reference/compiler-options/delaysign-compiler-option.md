---
title: -delaysign (opções do compilador C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518324"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="8b888-102">-delaysign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="8b888-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="8b888-103">Essa opção faz com que o compilador reserve espaço no arquivo de saída para que uma assinatura digital possa ser adicionada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="8b888-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="8b888-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b888-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="8b888-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b888-105">Arguments</span></span>

<span data-ttu-id="8b888-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8b888-106">`+` &#124; `-`</span></span>

<span data-ttu-id="8b888-107">Use **-delaysign-** se você quiser um assembly totalmente assinado.</span><span class="sxs-lookup"><span data-stu-id="8b888-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="8b888-108">Use **-delaysign+** se você apenas desejar colocar a chave pública no assembly.</span><span class="sxs-lookup"><span data-stu-id="8b888-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="8b888-109">O padrão é **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="8b888-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="8b888-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b888-110">Remarks</span></span>

<span data-ttu-id="8b888-111">A opção **-delaysign** não tem nenhum efeito a menos que seja usada com [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="8b888-111">The **-delaysign** option has no effect unless used with [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="8b888-112">As opções **-delaysign** e **-publicsign** são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="8b888-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="8b888-113">Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular.</span><span class="sxs-lookup"><span data-stu-id="8b888-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="8b888-114">Essa operação cria uma assinatura digital que é armazenada no arquivo que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="8b888-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="8b888-115">Quando um assembly é assinado com atraso, o compilador não calcula e armazena a assinatura, mas reserva o espaço no arquivo, de forma que a assinatura possa ser adicionada depois.</span><span class="sxs-lookup"><span data-stu-id="8b888-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="8b888-116">Por exemplo, o uso de **-delaysign+** permite que um testador coloque o assembly no cache global.</span><span class="sxs-lookup"><span data-stu-id="8b888-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="8b888-117">Após o teste, é possível assinar completamente o assembly, colocando a chave particular no assembly com o utilitário [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="8b888-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="8b888-118">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="8b888-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8b888-119">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b888-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="8b888-120">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="8b888-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="8b888-121">Modifique a propriedade **Apenas adiar a assinatura**.</span><span class="sxs-lookup"><span data-stu-id="8b888-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="8b888-122">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b888-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b888-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b888-123">See Also</span></span>

- [<span data-ttu-id="8b888-124">Opção -publicsign do C#</span><span class="sxs-lookup"><span data-stu-id="8b888-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)  
- [<span data-ttu-id="8b888-125">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="8b888-125">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="8b888-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="8b888-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
