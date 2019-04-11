---
title: -deterministic
ms.date: 04/11/2018
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
ms.openlocfilehash: 95c9add0521208ef04ff47c071a2e04abc968f27
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480632"
---
# <a name="-deterministic"></a><span data-ttu-id="fdf05-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="fdf05-102">-deterministic</span></span>

<span data-ttu-id="fdf05-103">Faz com que o compilador produza um assembly cuja saída byte a byte é idêntica entre compilações para entradas idênticas.</span><span class="sxs-lookup"><span data-stu-id="fdf05-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="fdf05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdf05-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="fdf05-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdf05-105">Remarks</span></span>

<span data-ttu-id="fdf05-106">Por padrão, a saída do compilador de um determinado conjunto de entradas é exclusiva, uma vez que o compilador adiciona um carimbo de data/hora e um GUID gerado com base em números aleatórios.</span><span class="sxs-lookup"><span data-stu-id="fdf05-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="fdf05-107">Use a opção `-deterministic` para produzir um *assembly determinística*, cujo conteúdo binário seja idêntico entre compilações, desde que a entrada permaneça a mesma.</span><span class="sxs-lookup"><span data-stu-id="fdf05-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="fdf05-108">O compilador considera as seguintes entradas com a finalidade de determinismo:</span><span class="sxs-lookup"><span data-stu-id="fdf05-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="fdf05-109">A sequência de parâmetros de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="fdf05-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="fdf05-110">O conteúdo do arquivo de resposta .rsp do compilador.</span><span class="sxs-lookup"><span data-stu-id="fdf05-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="fdf05-111">A versão precisa do compilador usado e seus assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="fdf05-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="fdf05-112">O caminho do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="fdf05-112">The current directory path.</span></span>
- <span data-ttu-id="fdf05-113">O conteúdo binário de todos os arquivos passados explicitamente para o compilador direta ou indiretamente, incluindo:</span><span class="sxs-lookup"><span data-stu-id="fdf05-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="fdf05-114">Arquivos de origem</span><span class="sxs-lookup"><span data-stu-id="fdf05-114">Source files</span></span>
  - <span data-ttu-id="fdf05-115">Assemblies referenciados</span><span class="sxs-lookup"><span data-stu-id="fdf05-115">Referenced assemblies</span></span>
  - <span data-ttu-id="fdf05-116">Módulos referenciados</span><span class="sxs-lookup"><span data-stu-id="fdf05-116">Referenced modules</span></span>
  - <span data-ttu-id="fdf05-117">Recursos</span><span class="sxs-lookup"><span data-stu-id="fdf05-117">Resources</span></span>
  - <span data-ttu-id="fdf05-118">O arquivo de chave de nome forte</span><span class="sxs-lookup"><span data-stu-id="fdf05-118">The strong name key file</span></span>
  - <span data-ttu-id="fdf05-119">@ arquivos de resposta</span><span class="sxs-lookup"><span data-stu-id="fdf05-119">@ response files</span></span>
  - <span data-ttu-id="fdf05-120">Analisadores</span><span class="sxs-lookup"><span data-stu-id="fdf05-120">Analyzers</span></span>
  - <span data-ttu-id="fdf05-121">Conjuntos de regras</span><span class="sxs-lookup"><span data-stu-id="fdf05-121">Rulesets</span></span>
  - <span data-ttu-id="fdf05-122">Arquivos adicionais que podem ser usados por analisadores</span><span class="sxs-lookup"><span data-stu-id="fdf05-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="fdf05-123">A cultura atual (para o idioma no qual as mensagens de diagnóstico e exceção são produzidas).</span><span class="sxs-lookup"><span data-stu-id="fdf05-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="fdf05-124">A codificação padrão (ou a página de código atual) se a codificação não for especificada.</span><span class="sxs-lookup"><span data-stu-id="fdf05-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="fdf05-125">A existência, a inexistência e o conteúdo dos arquivos em caminhos de pesquisa do compilador (especificados, por exemplo, por `/lib` ou `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="fdf05-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="fdf05-126">A plataforma CLR na qual o compilador é executado.</span><span class="sxs-lookup"><span data-stu-id="fdf05-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="fdf05-127">O valor de `%LIBPATH%`, que pode afetar o carregamento de dependência do analisador.</span><span class="sxs-lookup"><span data-stu-id="fdf05-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="fdf05-128">Quando as fontes estão disponíveis publicamente, a compilação determinística pode ser usada para estabelecer se um binário é compilado de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="fdf05-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="fdf05-129">Isso também pode ser útil em um sistema de compilação contínua para determinar se as etapas de compilação dependentes de alterações para um binário precisam ser executadas.</span><span class="sxs-lookup"><span data-stu-id="fdf05-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdf05-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdf05-130">See also</span></span>

- [<span data-ttu-id="fdf05-131">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fdf05-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fdf05-132">Linhas de comando de compilação de exemplo</span><span class="sxs-lookup"><span data-stu-id="fdf05-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
