---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512532"
---
# <a name="trace-type-summary"></a><span data-ttu-id="9ad6c-102">Resumo de tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9ad6c-102">Trace Type Summary</span></span>
<span data-ttu-id="9ad6c-103">[Níveis de origem](https://go.microsoft.com/fwlink/?LinkID=94943) define vários níveis de rastreamento: crítico, erro, aviso, informações e detalhado, bem como fornece a descrição do `ActivityTracing` sinalizador, que alterna a saída de rastreamento de eventos de transferência de limite e a atividade.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="9ad6c-104">Você também pode examinar [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos de <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="9ad6c-105">A tabela a seguir lista os mais importantes.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="9ad6c-106">Tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9ad6c-106">Trace Type</span></span>|<span data-ttu-id="9ad6c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ad6c-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="9ad6c-108">Crítico</span><span class="sxs-lookup"><span data-stu-id="9ad6c-108">Critical</span></span>|<span data-ttu-id="9ad6c-109">Erro fatal ou falha do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="9ad6c-110">Erro</span><span class="sxs-lookup"><span data-stu-id="9ad6c-110">Error</span></span>|<span data-ttu-id="9ad6c-111">Erro recuperável.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-111">Recoverable error.</span></span>|  
|<span data-ttu-id="9ad6c-112">Aviso</span><span class="sxs-lookup"><span data-stu-id="9ad6c-112">Warning</span></span>|<span data-ttu-id="9ad6c-113">Mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-113">Informational message.</span></span>|  
|<span data-ttu-id="9ad6c-114">Informações</span><span class="sxs-lookup"><span data-stu-id="9ad6c-114">Information</span></span>|<span data-ttu-id="9ad6c-115">Problema não crítico.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="9ad6c-116">Detalhado</span><span class="sxs-lookup"><span data-stu-id="9ad6c-116">Verbose</span></span>|<span data-ttu-id="9ad6c-117">Rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-117">Debugging trace.</span></span>|  
|<span data-ttu-id="9ad6c-118">Início</span><span class="sxs-lookup"><span data-stu-id="9ad6c-118">Start</span></span>|<span data-ttu-id="9ad6c-119">Início de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9ad6c-120">Suspender</span><span class="sxs-lookup"><span data-stu-id="9ad6c-120">Suspend</span></span>|<span data-ttu-id="9ad6c-121">Suspensão de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9ad6c-122">Resume</span><span class="sxs-lookup"><span data-stu-id="9ad6c-122">Resume</span></span>|<span data-ttu-id="9ad6c-123">Continuação de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9ad6c-124">Stop</span><span class="sxs-lookup"><span data-stu-id="9ad6c-124">Stop</span></span>|<span data-ttu-id="9ad6c-125">Parada de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9ad6c-126">Transferir</span><span class="sxs-lookup"><span data-stu-id="9ad6c-126">Transfer</span></span>|<span data-ttu-id="9ad6c-127">Alteração da identidade de correlação.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="9ad6c-128">Uma atividade é definida como uma combinação dos tipos de rastreamento acima.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="9ad6c-129">O exemplo a seguir é uma expressão regular que define uma atividade ideal em um escopo local (origem de rastreamento),</span><span class="sxs-lookup"><span data-stu-id="9ad6c-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="9ad6c-130">Isso significa que uma atividade deve satisfazer as condições a seguir.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="9ad6c-131">Ele deve iniciar e parar, respectivamente, rastreamentos de início e parada</span><span class="sxs-lookup"><span data-stu-id="9ad6c-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="9ad6c-132">Ele deve ter um rastreamento de transferência imediatamente anterior a um rastreamento de suspensão ou retomada</span><span class="sxs-lookup"><span data-stu-id="9ad6c-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="9ad6c-133">Ele não deve ter os rastreamentos entre os rastreamentos de suspender e continuar se existirem tais rastreamentos</span><span class="sxs-lookup"><span data-stu-id="9ad6c-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="9ad6c-134">Ele pode ter qualquer e a quantidade de rastreamentos de crítico/erro/aviso / / detalhado/transferência de informações, desde que as condições anteriores forem observadas</span><span class="sxs-lookup"><span data-stu-id="9ad6c-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="9ad6c-135">O exemplo a seguir é uma expressão regular que define uma atividade ideal no escopo global,</span><span class="sxs-lookup"><span data-stu-id="9ad6c-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="9ad6c-136">com o R que é a expressão regular para uma atividade no escopo local.</span><span class="sxs-lookup"><span data-stu-id="9ad6c-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="9ad6c-137">Isso se traduz em,</span><span class="sxs-lookup"><span data-stu-id="9ad6c-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
