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
ms.openlocfilehash: 9fdc02c22d9d8c8a709155e43a17ebf0d86dfd69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970438"
---
# <a name="-delaysign-c-compiler-options"></a><span data-ttu-id="f775a-102">-delaysign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="f775a-102">-delaysign (C# Compiler Options)</span></span>

<span data-ttu-id="f775a-103">Essa opção faz com que o compilador reserve espaço no arquivo de saída para que uma assinatura digital possa ser adicionada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="f775a-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>

## <a name="syntax"></a><span data-ttu-id="f775a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f775a-104">Syntax</span></span>

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a><span data-ttu-id="f775a-105">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f775a-105">Arguments</span></span>

<span data-ttu-id="f775a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f775a-106">`+` &#124; `-`</span></span>

<span data-ttu-id="f775a-107">Use **-delaysign-** se você quiser um assembly totalmente assinado.</span><span class="sxs-lookup"><span data-stu-id="f775a-107">Use **-delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="f775a-108">Use **-delaysign+** se você apenas desejar colocar a chave pública no assembly.</span><span class="sxs-lookup"><span data-stu-id="f775a-108">Use **-delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="f775a-109">O padrão é **-delaysign-**.</span><span class="sxs-lookup"><span data-stu-id="f775a-109">The default is **-delaysign-**.</span></span>

## <a name="remarks"></a><span data-ttu-id="f775a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f775a-110">Remarks</span></span>

<span data-ttu-id="f775a-111">A opção **-delaysign** não tem efeito a menos que seja usada com [-keyfile](./keyfile-compiler-option.md) ou [-keycontainer](./keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f775a-111">The **-delaysign** option has no effect unless used with [-keyfile](./keyfile-compiler-option.md) or [-keycontainer](./keycontainer-compiler-option.md).</span></span>

<span data-ttu-id="f775a-112">As opções **-delaysign** e **-publicsign** são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="f775a-112">The **-delaysign** and **-publicsign** options are mutually exclusive.</span></span>

<span data-ttu-id="f775a-113">Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular.</span><span class="sxs-lookup"><span data-stu-id="f775a-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="f775a-114">Essa operação cria uma assinatura digital que é armazenada no arquivo que contém o manifesto.</span><span class="sxs-lookup"><span data-stu-id="f775a-114">That operation creates a digital signature which is stored in the file that contains the manifest.</span></span> <span data-ttu-id="f775a-115">Quando um assembly é assinado com atraso, o compilador não calcula e armazena a assinatura, mas reserva o espaço no arquivo, de forma que a assinatura possa ser adicionada depois.</span><span class="sxs-lookup"><span data-stu-id="f775a-115">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>

<span data-ttu-id="f775a-116">Por exemplo, o uso de **-delaysign+** permite que um testador coloque o assembly no cache global.</span><span class="sxs-lookup"><span data-stu-id="f775a-116">For example, using **-delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="f775a-117">Após o teste, é possível assinar completamente o assembly, colocando a chave particular no assembly com o utilitário [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="f775a-117">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](../../../framework/tools/al-exe-assembly-linker.md) utility.</span></span>

<span data-ttu-id="f775a-118">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../standard/assembly/create-use-strong-named.md) e [Atraso na Assinatura de um Assembly](../../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="f775a-118">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f775a-119">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f775a-119">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="f775a-120">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="f775a-120">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="f775a-121">Modifique a propriedade **Apenas adiar a assinatura**.</span><span class="sxs-lookup"><span data-stu-id="f775a-121">Modify the **Delay sign only** property.</span></span>

<span data-ttu-id="f775a-122">Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span><span class="sxs-lookup"><span data-stu-id="f775a-122">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f775a-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="f775a-123">See also</span></span>

- [<span data-ttu-id="f775a-124">Opção -publicsign do C#</span><span class="sxs-lookup"><span data-stu-id="f775a-124">C# -publicsign option</span></span>](publicsign-compiler-option.md)
- [<span data-ttu-id="f775a-125">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="f775a-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="f775a-126">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="f775a-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
