---
title: Visão geral das ferramentas de diagnóstico – .NET Core
description: Uma visão geral das ferramentas e das técnicas disponíveis para diagnosticar aplicativos .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974144"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="7f53b-103">Quais ferramentas de diagnóstico estão disponíveis no .NET Core?</span><span class="sxs-lookup"><span data-stu-id="7f53b-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="7f53b-104">O software nem sempre se comporta como esperado, mas o .NET Core tem ferramentas e APIs que ajudarão você a diagnosticar esses problemas de maneira rápida e eficaz.</span><span class="sxs-lookup"><span data-stu-id="7f53b-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="7f53b-105">Este artigo ajuda a identificar as diversas ferramentas de que você precisa.</span><span class="sxs-lookup"><span data-stu-id="7f53b-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggersmanaged-debuggersmd"></a>[<span data-ttu-id="7f53b-106">Depuradores gerenciados</span><span class="sxs-lookup"><span data-stu-id="7f53b-106">Managed debuggers</span></span>](managed-debuggers.md)
<span data-ttu-id="7f53b-107">Os depuradores gerenciados permitem que você interaja com seu programa.</span><span class="sxs-lookup"><span data-stu-id="7f53b-107">Managed debuggers allow you to interact with your program.</span></span> <span data-ttu-id="7f53b-108">Pausar, executar incrementalmente, examinar e retomar fornecem informações sobre o comportamento do seu código.</span><span class="sxs-lookup"><span data-stu-id="7f53b-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="7f53b-109">Um depurador é a primeira opção para diagnosticar problemas funcionais que podem ser facilmente reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="7f53b-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracinglogging-tracingmd"></a>[<span data-ttu-id="7f53b-110">Registro em log e rastreamento</span><span class="sxs-lookup"><span data-stu-id="7f53b-110">Logging and tracing</span></span>](logging-tracing.md)
<span data-ttu-id="7f53b-111">O registro em log e o rastreamento são técnicas relacionadas.</span><span class="sxs-lookup"><span data-stu-id="7f53b-111">Logging and tracing are related techniques.</span></span> <span data-ttu-id="7f53b-112">Eles se referem ao código de instrumentação para criar arquivos de log.</span><span class="sxs-lookup"><span data-stu-id="7f53b-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="7f53b-113">Os arquivos registram os detalhes do que um programa faz.</span><span class="sxs-lookup"><span data-stu-id="7f53b-113">The files record the details of what a program does.</span></span> <span data-ttu-id="7f53b-114">Esses detalhes podem ser usados para diagnosticar os problemas mais complexos.</span><span class="sxs-lookup"><span data-stu-id="7f53b-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="7f53b-115">Quando aliados aos carimbos de data/hora, essas técnicas também são valiosas para as investigações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7f53b-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testingtestingindexmd"></a>[<span data-ttu-id="7f53b-116">Teste de unidade</span><span class="sxs-lookup"><span data-stu-id="7f53b-116">Unit testing</span></span>](../testing/index.md)
<span data-ttu-id="7f53b-117">O teste de unidade é um componente-chave da integração contínua e da implantação de um software de alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="7f53b-117">Unit testing is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="7f53b-118">Os testes de unidade são projetados para fornecer um aviso antecipado quando você interrompe algo.</span><span class="sxs-lookup"><span data-stu-id="7f53b-118">Unit tests are designed to give you an early warning when you break something.</span></span>
