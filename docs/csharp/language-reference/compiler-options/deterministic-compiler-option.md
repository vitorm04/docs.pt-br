---
description: -deterministic (Opções do Compilador C#)
title: -deterministic (Opções do Compilador C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: 9d0bcc2957e5a666c21cdc2ce61e74fc90fe3530
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125820"
---
# <a name="-deterministic"></a><span data-ttu-id="89715-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="89715-103">-deterministic</span></span>

<span data-ttu-id="89715-104">Faz com que o compilador produza um assembly cuja saída byte a byte é idêntica entre compilações para entradas idênticas.</span><span class="sxs-lookup"><span data-stu-id="89715-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="89715-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89715-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="89715-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="89715-106">Remarks</span></span>

<span data-ttu-id="89715-107">Por padrão, a saída do compilador de um determinado conjunto de entradas é exclusiva, uma vez que o compilador adiciona um carimbo de data/hora e um GUID gerado com base em números aleatórios.</span><span class="sxs-lookup"><span data-stu-id="89715-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="89715-108">Use a opção `-deterministic` para produzir um *assembly determinística*, cujo conteúdo binário seja idêntico entre compilações, desde que a entrada permaneça a mesma.</span><span class="sxs-lookup"><span data-stu-id="89715-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="89715-109">O compilador considera as seguintes entradas com a finalidade de determinismo:</span><span class="sxs-lookup"><span data-stu-id="89715-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="89715-110">A sequência de parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="89715-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="89715-111">O conteúdo do arquivo de resposta .rsp do compilador.</span><span class="sxs-lookup"><span data-stu-id="89715-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="89715-112">A versão precisa do compilador usado e seus assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="89715-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="89715-113">O caminho do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="89715-113">The current directory path.</span></span>
- <span data-ttu-id="89715-114">O conteúdo binário de todos os arquivos passados explicitamente para o compilador direta ou indiretamente, incluindo:</span><span class="sxs-lookup"><span data-stu-id="89715-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="89715-115">Arquivos de origem</span><span class="sxs-lookup"><span data-stu-id="89715-115">Source files</span></span>
  - <span data-ttu-id="89715-116">Assemblies referenciados</span><span class="sxs-lookup"><span data-stu-id="89715-116">Referenced assemblies</span></span>
  - <span data-ttu-id="89715-117">Módulos referenciados</span><span class="sxs-lookup"><span data-stu-id="89715-117">Referenced modules</span></span>
  - <span data-ttu-id="89715-118">Recursos</span><span class="sxs-lookup"><span data-stu-id="89715-118">Resources</span></span>
  - <span data-ttu-id="89715-119">O arquivo de chave de nome forte</span><span class="sxs-lookup"><span data-stu-id="89715-119">The strong name key file</span></span>
  - <span data-ttu-id="89715-120">@ arquivos de resposta</span><span class="sxs-lookup"><span data-stu-id="89715-120">@ response files</span></span>
  - <span data-ttu-id="89715-121">Analisadores</span><span class="sxs-lookup"><span data-stu-id="89715-121">Analyzers</span></span>
  - <span data-ttu-id="89715-122">Conjuntos de regras</span><span class="sxs-lookup"><span data-stu-id="89715-122">Rulesets</span></span>
  - <span data-ttu-id="89715-123">Arquivos adicionais que podem ser usados por analisadores</span><span class="sxs-lookup"><span data-stu-id="89715-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="89715-124">A cultura atual (para o idioma no qual as mensagens de diagnóstico e exceção são produzidas).</span><span class="sxs-lookup"><span data-stu-id="89715-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="89715-125">A codificação padrão (ou a página de código atual) se a codificação não for especificada.</span><span class="sxs-lookup"><span data-stu-id="89715-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="89715-126">A existência, a inexistência e o conteúdo dos arquivos em caminhos de pesquisa do compilador (especificados, por exemplo, por `-lib` ou `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="89715-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="89715-127">A plataforma CLR na qual o compilador é executado.</span><span class="sxs-lookup"><span data-stu-id="89715-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="89715-128">O valor de `%LIBPATH%`, que pode afetar o carregamento de dependência do analisador.</span><span class="sxs-lookup"><span data-stu-id="89715-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="89715-129">Quando as fontes estão disponíveis publicamente, a compilação determinística pode ser usada para estabelecer se um binário é compilado de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="89715-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="89715-130">Isso também pode ser útil em um sistema de compilação contínua para determinar se as etapas de compilação dependentes de alterações para um binário precisam ser executadas.</span><span class="sxs-lookup"><span data-stu-id="89715-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="89715-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="89715-131">See also</span></span>

- [<span data-ttu-id="89715-132">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="89715-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="89715-133">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="89715-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
