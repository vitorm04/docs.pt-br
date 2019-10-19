---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582866"
---
# <a name="-refout-visual-basic"></a><span data-ttu-id="79444-102">-refout (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79444-102">-refout (Visual Basic)</span></span>

<span data-ttu-id="79444-103">A opção **-refout** especifica um caminho de arquivo em que o assembly de referência deve ser gerado.</span><span class="sxs-lookup"><span data-stu-id="79444-103">The **-refout** option specifies a file path where the reference assembly should be output.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="79444-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="79444-104">Syntax</span></span>

```console
-refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="79444-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="79444-105">Arguments</span></span>

`filepath`  
<span data-ttu-id="79444-106">O caminho e o nome do arquivo do assembly de referência.</span><span class="sxs-lookup"><span data-stu-id="79444-106">The path and filename of the reference assembly.</span></span> <span data-ttu-id="79444-107">Em geral, ele deve estar em uma subpasta do assembly primário.</span><span class="sxs-lookup"><span data-stu-id="79444-107">It should generally be in a sub-folder of the primary assembly.</span></span> <span data-ttu-id="79444-108">A convenção recomendada (usada pelo MSBuild) é colocar o assembly de referência em uma subpasta "ref/" em relação ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="79444-108">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span> <span data-ttu-id="79444-109">Todas as pastas no `filepath` devem existir; o compilador não os cria.</span><span class="sxs-lookup"><span data-stu-id="79444-109">All folders in `filepath` must exist; the compiler does not create them.</span></span>

## <a name="remarks"></a><span data-ttu-id="79444-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="79444-110">Remarks</span></span>

<span data-ttu-id="79444-111">Visual Basic dá suporte à opção de `-refout` a partir da versão 15,3.</span><span class="sxs-lookup"><span data-stu-id="79444-111">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="79444-112">Os assemblies de referência são assemblies somente de metadados que contêm metadados, mas nenhum código de implementação.</span><span class="sxs-lookup"><span data-stu-id="79444-112">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="79444-113">Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="79444-113">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="79444-114">Seus corpos de método são substituídos por uma única instrução de `throw null`.</span><span class="sxs-lookup"><span data-stu-id="79444-114">Their method bodies are replaced with a single `throw null` statement.</span></span> <span data-ttu-id="79444-115">O motivo para usar `throw null` corpos de método (em oposição a nenhum corpo) é para que PEVerify possa executar e passar (Validando assim a integridade dos metadados).</span><span class="sxs-lookup"><span data-stu-id="79444-115">The reason for using `throw null` method bodies (as opposed to no bodies) is so that PEVerify can run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="79444-116">Os assemblies de referência incluem um atributo [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) no nível do assembly.</span><span class="sxs-lookup"><span data-stu-id="79444-116">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="79444-117">Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo).</span><span class="sxs-lookup"><span data-stu-id="79444-117">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="79444-118">Devido a esse atributo, os tempos de execução se recusam a carregar assemblies de referência para execução (mas eles ainda podem ser carregados em um contexto somente de reflexão).</span><span class="sxs-lookup"><span data-stu-id="79444-118">Because of this attribute, runtimes refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="79444-119">As ferramentas que refletem em assemblies precisam garantir que carreguem assemblies de referência como somente reflexão; caso contrário, o tempo de execução gera um <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="79444-119">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="79444-120">As opções `-refout` e [`-refonly`](refonly-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="79444-120">The `-refout` and [`-refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="79444-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79444-121">See also</span></span>

- [<span data-ttu-id="79444-122">/refonly</span><span class="sxs-lookup"><span data-stu-id="79444-122">-refonly</span></span>](refonly-compiler-option.md)
- [<span data-ttu-id="79444-123">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="79444-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="79444-124">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="79444-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
