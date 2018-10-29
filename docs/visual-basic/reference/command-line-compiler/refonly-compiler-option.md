---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b22fb9ae24a04d9fe530811bf764352199c31813
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200804"
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="21b8d-102">-refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21b8d-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="21b8d-103">O **- refonly** opção indica que a saída primária da compilação deve ser um assembly de referência em vez de um assembly de implementação.</span><span class="sxs-lookup"><span data-stu-id="21b8d-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="21b8d-104">O parâmetro `-refonly` silenciosamente desabilita a geração de PDBs, uma vez que assemblies de referência não podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="21b8d-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="21b8d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21b8d-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="21b8d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="21b8d-106">Remarks</span></span>

<span data-ttu-id="21b8d-107">Visual Basic oferece suporte a `-refout` alternar a partir da versão 15.3.</span><span class="sxs-lookup"><span data-stu-id="21b8d-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="21b8d-108">Assemblies de referência são assemblies somente de metadados que contêm metadados, mas nenhum código de implementação.</span><span class="sxs-lookup"><span data-stu-id="21b8d-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="21b8d-109">Eles incluem informações de tipo e membro para tudo, exceto tipos anônimos.</span><span class="sxs-lookup"><span data-stu-id="21b8d-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="21b8d-110">O motivo para usar corpos `throw null` (em vez de nenhum corpo) é que PEVerify poderia ser executado e passado (validando, assim, a integridade dos metadados).</span><span class="sxs-lookup"><span data-stu-id="21b8d-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="21b8d-111">Assemblies de referência incluem um nível de conjunto [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atributo.</span><span class="sxs-lookup"><span data-stu-id="21b8d-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="21b8d-112">Esse atributo pode ser especificado na origem (assim, o compilador não precisará sintetizá-lo).</span><span class="sxs-lookup"><span data-stu-id="21b8d-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="21b8d-113">Devido a esse atributo, tempos de execução se recusarão a carregar assemblies de referência para a execução (mas ainda podem ser carregados em um contexto de somente reflexão).</span><span class="sxs-lookup"><span data-stu-id="21b8d-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="21b8d-114">As ferramentas que refletem nos assemblies precisam garantir que elas carreguem assemblies de referência como somente reflexão; Caso contrário, o tempo de execução gera uma <xref:System.BadImageFormatException>.</span><span class="sxs-lookup"><span data-stu-id="21b8d-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="21b8d-115">As opções `-refonly` e [`-refout`](refout-compiler-option.md) são mutualmente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="21b8d-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="21b8d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21b8d-116">See also</span></span>
<span data-ttu-id="21b8d-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="21b8d-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="21b8d-118">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21b8d-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="21b8d-119">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="21b8d-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
