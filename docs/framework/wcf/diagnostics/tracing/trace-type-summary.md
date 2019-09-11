---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856005"
---
# <a name="trace-type-summary"></a><span data-ttu-id="a8942-102">Resumo de tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="a8942-102">Trace Type Summary</span></span>
<span data-ttu-id="a8942-103">[Os níveis de origem](https://go.microsoft.com/fwlink/?LinkID=94943) definem vários níveis de rastreamento: Crítico, erro, aviso, informações e detalhado, bem como fornece a `ActivityTracing` descrição do sinalizador, que alterna a saída de eventos de limite de rastreamento e de transferência de atividade.</span><span class="sxs-lookup"><span data-stu-id="a8942-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="a8942-104">Você também pode examinar [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="a8942-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="a8942-105">A tabela a seguir lista os mais importantes.</span><span class="sxs-lookup"><span data-stu-id="a8942-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="a8942-106">Tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="a8942-106">Trace Type</span></span>|<span data-ttu-id="a8942-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8942-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="a8942-108">Crítica</span><span class="sxs-lookup"><span data-stu-id="a8942-108">Critical</span></span>|<span data-ttu-id="a8942-109">Erro fatal ou falha do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8942-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="a8942-110">Erro</span><span class="sxs-lookup"><span data-stu-id="a8942-110">Error</span></span>|<span data-ttu-id="a8942-111">Erro recuperável.</span><span class="sxs-lookup"><span data-stu-id="a8942-111">Recoverable error.</span></span>|  
|<span data-ttu-id="a8942-112">Aviso</span><span class="sxs-lookup"><span data-stu-id="a8942-112">Warning</span></span>|<span data-ttu-id="a8942-113">Mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="a8942-113">Informational message.</span></span>|  
|<span data-ttu-id="a8942-114">Informações</span><span class="sxs-lookup"><span data-stu-id="a8942-114">Information</span></span>|<span data-ttu-id="a8942-115">Problema não crítico.</span><span class="sxs-lookup"><span data-stu-id="a8942-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="a8942-116">Detalhado</span><span class="sxs-lookup"><span data-stu-id="a8942-116">Verbose</span></span>|<span data-ttu-id="a8942-117">Rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="a8942-117">Debugging trace.</span></span>|  
|<span data-ttu-id="a8942-118">Início</span><span class="sxs-lookup"><span data-stu-id="a8942-118">Start</span></span>|<span data-ttu-id="a8942-119">Início de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="a8942-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a8942-120">Suspend</span><span class="sxs-lookup"><span data-stu-id="a8942-120">Suspend</span></span>|<span data-ttu-id="a8942-121">Suspensão de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="a8942-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a8942-122">Continuar</span><span class="sxs-lookup"><span data-stu-id="a8942-122">Resume</span></span>|<span data-ttu-id="a8942-123">Retomada de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="a8942-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a8942-124">Parar</span><span class="sxs-lookup"><span data-stu-id="a8942-124">Stop</span></span>|<span data-ttu-id="a8942-125">Interrupção de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="a8942-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="a8942-126">Transferir</span><span class="sxs-lookup"><span data-stu-id="a8942-126">Transfer</span></span>|<span data-ttu-id="a8942-127">Alteração da identidade de correlação.</span><span class="sxs-lookup"><span data-stu-id="a8942-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="a8942-128">Uma atividade é definida como uma combinação dos tipos de rastreamento acima.</span><span class="sxs-lookup"><span data-stu-id="a8942-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="a8942-129">Veja a seguir uma expressão regular que define uma atividade ideal em um escopo local (origem do rastreamento),</span><span class="sxs-lookup"><span data-stu-id="a8942-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="a8942-130">Isso significa que uma atividade deve atender às condições a seguir.</span><span class="sxs-lookup"><span data-stu-id="a8942-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="a8942-131">Ele deve iniciar e parar respectivamente por um rastreamento de iniciar e parar</span><span class="sxs-lookup"><span data-stu-id="a8942-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="a8942-132">Ele deve ter um rastreamento de transferência imediatamente antes de um rastreamento de suspensão ou retomada</span><span class="sxs-lookup"><span data-stu-id="a8942-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="a8942-133">Ele não deve ter nenhum rastreamento entre os rastreamentos suspender e retomar se esses rastreamentos existirem</span><span class="sxs-lookup"><span data-stu-id="a8942-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="a8942-134">Ele pode ter qualquer e quantos rastreamentos crítico/erro/aviso/informações/detalhados/de transferência, desde que as condições anteriores sejam observadas</span><span class="sxs-lookup"><span data-stu-id="a8942-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="a8942-135">Veja a seguir uma expressão regular que define uma atividade ideal no escopo global,</span><span class="sxs-lookup"><span data-stu-id="a8942-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="a8942-136">o R é a expressão regular para uma atividade no escopo local.</span><span class="sxs-lookup"><span data-stu-id="a8942-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="a8942-137">Isso se traduz em,</span><span class="sxs-lookup"><span data-stu-id="a8942-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
