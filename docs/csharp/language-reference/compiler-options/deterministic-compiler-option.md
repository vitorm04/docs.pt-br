---
title: -deterministic (Opções do Compilador C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77c14a1c3a4ba11b8ae6556be4f1c3c0cd42788
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202928"
---
# <a name="-deterministic"></a><span data-ttu-id="7cf39-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="7cf39-102">-deterministic</span></span>

<span data-ttu-id="7cf39-103">Faz com que o compilador produza um assembly cuja saída byte a byte é idêntica entre compilações para entradas idênticas.</span><span class="sxs-lookup"><span data-stu-id="7cf39-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="7cf39-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7cf39-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="7cf39-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7cf39-105">Remarks</span></span>

<span data-ttu-id="7cf39-106">Por padrão, a saída do compilador de um determinado conjunto de entradas é exclusiva, uma vez que o compilador adiciona um carimbo de data/hora e um GUID gerado com base em números aleatórios.</span><span class="sxs-lookup"><span data-stu-id="7cf39-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="7cf39-107">Use a opção `-deterministic` para produzir um *assembly determinística*, cujo conteúdo binário seja idêntico entre compilações, desde que a entrada permaneça a mesma.</span><span class="sxs-lookup"><span data-stu-id="7cf39-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="7cf39-108">O compilador considera as seguintes entradas com a finalidade de determinismo:</span><span class="sxs-lookup"><span data-stu-id="7cf39-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="7cf39-109">A sequência de parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7cf39-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="7cf39-110">O conteúdo do arquivo de resposta .rsp do compilador.</span><span class="sxs-lookup"><span data-stu-id="7cf39-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="7cf39-111">A versão precisa do compilador usado e seus assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="7cf39-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="7cf39-112">O caminho do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="7cf39-112">The current directory path.</span></span>
- <span data-ttu-id="7cf39-113">O conteúdo binário de todos os arquivos passados explicitamente para o compilador direta ou indiretamente, incluindo:</span><span class="sxs-lookup"><span data-stu-id="7cf39-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="7cf39-114">Arquivos de origem</span><span class="sxs-lookup"><span data-stu-id="7cf39-114">Source files</span></span>
  - <span data-ttu-id="7cf39-115">Assemblies referenciados</span><span class="sxs-lookup"><span data-stu-id="7cf39-115">Referenced assemblies</span></span>
  - <span data-ttu-id="7cf39-116">Módulos referenciados</span><span class="sxs-lookup"><span data-stu-id="7cf39-116">Referenced modules</span></span>
  - <span data-ttu-id="7cf39-117">Recursos</span><span class="sxs-lookup"><span data-stu-id="7cf39-117">Resources</span></span>
  - <span data-ttu-id="7cf39-118">O arquivo de chave de nome forte</span><span class="sxs-lookup"><span data-stu-id="7cf39-118">The strong name key file</span></span>
  - <span data-ttu-id="7cf39-119">@ arquivos de resposta</span><span class="sxs-lookup"><span data-stu-id="7cf39-119">@ response files</span></span>
  - <span data-ttu-id="7cf39-120">Analisadores</span><span class="sxs-lookup"><span data-stu-id="7cf39-120">Analyzers</span></span>
  - <span data-ttu-id="7cf39-121">Conjuntos de regras</span><span class="sxs-lookup"><span data-stu-id="7cf39-121">Rulesets</span></span>
  - <span data-ttu-id="7cf39-122">Arquivos adicionais que podem ser usados por analisadores</span><span class="sxs-lookup"><span data-stu-id="7cf39-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="7cf39-123">A cultura atual (para o idioma no qual as mensagens de diagnóstico e exceção são produzidas).</span><span class="sxs-lookup"><span data-stu-id="7cf39-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="7cf39-124">A codificação padrão (ou a página de código atual) se a codificação não for especificada.</span><span class="sxs-lookup"><span data-stu-id="7cf39-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="7cf39-125">A existência, a inexistência e o conteúdo dos arquivos em caminhos de pesquisa do compilador (especificados, por exemplo, por `/lib` ou `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="7cf39-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="7cf39-126">A plataforma CLR na qual o compilador é executado.</span><span class="sxs-lookup"><span data-stu-id="7cf39-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="7cf39-127">O valor de `%LIBPATH%`, que pode afetar o carregamento de dependência do analisador.</span><span class="sxs-lookup"><span data-stu-id="7cf39-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="7cf39-128">Quando as fontes estão disponíveis publicamente, a compilação determinística pode ser usada para estabelecer se um binário é compilado de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="7cf39-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="7cf39-129">Isso também pode ser útil em um sistema de compilação contínua para determinar se as etapas de compilação dependentes de alterações para um binário precisam ser executadas.</span><span class="sxs-lookup"><span data-stu-id="7cf39-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cf39-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cf39-130">See also</span></span>

- [<span data-ttu-id="7cf39-131">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="7cf39-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7cf39-132">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="7cf39-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
