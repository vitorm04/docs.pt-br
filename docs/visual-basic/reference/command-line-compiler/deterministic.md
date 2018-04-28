---
title: -determinística
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273abf8811f04cd7f58599ce3421ca1f17c740d9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a><span data-ttu-id="c7e0c-102">-determinística</span><span class="sxs-lookup"><span data-stu-id="c7e0c-102">-deterministic</span></span>

<span data-ttu-id="c7e0c-103">Faz com que o compilador produzir um assembly cuja saída de byte a byte é idêntica em compilações para entradas idênticas.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="c7e0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7e0c-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="c7e0c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7e0c-105">Remarks</span></span>

<span data-ttu-id="c7e0c-106">Por padrão, a saída do compilador de um determinado conjunto de entradas é exclusiva, desde que o compilador adiciona um carimbo de hora e um GUID que é gerado a partir de números aleatórios.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="c7e0c-107">Usar o `-deterministic` opção para produzir um *assembly determinística*, cujo conteúdo binário é idêntico em compilações desde que a entrada permanece o mesmo.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="c7e0c-108">O compilador considera as seguintes entradas com a finalidade de determinismo:</span><span class="sxs-lookup"><span data-stu-id="c7e0c-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="c7e0c-109">A sequência de parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="c7e0c-110">O conteúdo do arquivo de resposta do compilador. rsp.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="c7e0c-111">A versão precisa do compilador usado e seus assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="c7e0c-112">O caminho do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-112">The current directory path.</span></span>
- <span data-ttu-id="c7e0c-113">O conteúdo binário de todos os arquivos passado explicitamente para o compilador direta ou indiretamente, incluindo:</span><span class="sxs-lookup"><span data-stu-id="c7e0c-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span> 
    - <span data-ttu-id="c7e0c-114">Arquivos de origem</span><span class="sxs-lookup"><span data-stu-id="c7e0c-114">Source files</span></span>
    - <span data-ttu-id="c7e0c-115">assemblies referenciados</span><span class="sxs-lookup"><span data-stu-id="c7e0c-115">Referenced assemblies</span></span>
    - <span data-ttu-id="c7e0c-116">Módulos referenciados</span><span class="sxs-lookup"><span data-stu-id="c7e0c-116">Referenced modules</span></span>
    - <span data-ttu-id="c7e0c-117">Recursos</span><span class="sxs-lookup"><span data-stu-id="c7e0c-117">Resources</span></span>
    - <span data-ttu-id="c7e0c-118">O arquivo de chave de nome forte</span><span class="sxs-lookup"><span data-stu-id="c7e0c-118">The strong name key file</span></span>
    - <span data-ttu-id="c7e0c-119">@ arquivos de resposta</span><span class="sxs-lookup"><span data-stu-id="c7e0c-119">@ response files</span></span>
    - <span data-ttu-id="c7e0c-120">Analisadores</span><span class="sxs-lookup"><span data-stu-id="c7e0c-120">Analyzers</span></span>
    - <span data-ttu-id="c7e0c-121">Conjuntos de regras</span><span class="sxs-lookup"><span data-stu-id="c7e0c-121">Rulesets</span></span>
    - <span data-ttu-id="c7e0c-122">Arquivos adicionais que podem ser usados por analisadores</span><span class="sxs-lookup"><span data-stu-id="c7e0c-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="c7e0c-123">A cultura atual (para o idioma no qual diagnóstico e a exceção são produzidas mensagens).</span><span class="sxs-lookup"><span data-stu-id="c7e0c-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="c7e0c-124">A codificação padrão (ou a página de código atual) se a codificação não for especificada.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="c7e0c-125">A existência, a não-existência e o conteúdo dos arquivos em caminhos de pesquisa do compilador (especificado, por exemplo, `/lib` ou `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="c7e0c-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="c7e0c-126">A plataforma CLR no qual o compilador é executado.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="c7e0c-127">O valor de `%LIBPATH%`, que pode afetar o carregamento de dependência do analisador.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="c7e0c-128">Quando fontes disponíveis publicamente, compilação determinística pode ser usada para estabelecer se um binário é compilado de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="c7e0c-129">Ele também pode ser útil em um sistema de compilação contínua para determinar se precisam de etapas de compilação que são dependentes de alterações em um binário a ser executado.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="c7e0c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7e0c-130">See Also</span></span>
[<span data-ttu-id="c7e0c-131">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7e0c-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
[<span data-ttu-id="c7e0c-132">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7e0c-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
