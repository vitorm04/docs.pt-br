---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21cea76f31bdf2ac5fcf434ee759f874f917617b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999462"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="2cac5-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cac5-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="2cac5-103">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="2cac5-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="2cac5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cac5-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="2cac5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2cac5-105">Arguments</span></span>

 <span data-ttu-id="2cac5-106">`filepath` O caminho e nome de arquivo do assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="2cac5-106">`filepath` The path and filename of the reference assembly.</span></span> <span data-ttu-id="2cac5-107">Em geral, ele deve ser em uma subpasta do assembly principal.</span><span class="sxs-lookup"><span data-stu-id="2cac5-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="2cac5-108">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="2cac5-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="2cac5-109">Todas as pastas no `filepath` deve existir; o compilador não criá-los.</span><span class="sxs-lookup"><span data-stu-id="2cac5-109">All folders in `filepath` must exist; the compiler does not create them.</span></span> 

## <a name="remarks"></a><span data-ttu-id="2cac5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cac5-110">Remarks</span></span>

<span data-ttu-id="2cac5-111">Visual Basic oferece suporte a `-refout` alternar a partir da versão 15.3.</span><span class="sxs-lookup"><span data-stu-id="2cac5-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="2cac5-112">Assemblies de referência são assemblies somente de metadados que contêm metadados, mas nenhum código de implementação.</span><span class="sxs-lookup"><span data-stu-id="2cac5-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="2cac5-113">Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="2cac5-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="2cac5-114">Seus corpos de método são substituídos por um único `throw null` instrução.</span><span class="sxs-lookup"><span data-stu-id="2cac5-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="2cac5-115">O motivo para usar `throw null` corpos de método (em vez de nenhum corpo) é que PEVerify pode executar e passar (Validando, assim, a integridade dos metadados).</span><span class="sxs-lookup"><span data-stu-id="2cac5-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="2cac5-116">Assemblies de referência incluem um nível de conjunto [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atributo.</span><span class="sxs-lookup"><span data-stu-id="2cac5-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="2cac5-117">Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo).</span><span class="sxs-lookup"><span data-stu-id="2cac5-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="2cac5-118">Devido a esse atributo, tempos de execução recusam carregar assemblies de referência para a execução (mas ainda podem ser carregados em um contexto de somente reflexão).</span><span class="sxs-lookup"><span data-stu-id="2cac5-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="2cac5-119">As ferramentas que refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão; Caso contrário, o tempo de execução gera uma <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="2cac5-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="2cac5-120">As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="2cac5-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cac5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cac5-121">See Also</span></span>
<span data-ttu-id="2cac5-122">[-refonly](refonly-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="2cac5-122">[-refonly](refonly-compiler-option.md) </span></span>  
[<span data-ttu-id="2cac5-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2cac5-123">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="2cac5-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cac5-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)  

