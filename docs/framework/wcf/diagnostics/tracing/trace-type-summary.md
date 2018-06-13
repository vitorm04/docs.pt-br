---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e3bc66753dd44e1dc4c7417caf593820300f69a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486029"
---
# <a name="trace-type-summary"></a><span data-ttu-id="357c6-102">Resumo de tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="357c6-102">Trace Type Summary</span></span>
<span data-ttu-id="357c6-103">[Níveis de origem](http://go.microsoft.com/fwlink/?LinkID=94943) define vários níveis de rastreamento: crítico, erro, aviso, informações e detalhado, bem como fornece descrição do `ActivityTracing` sinalizador, que alterna a saída de rastreamento de eventos de transferência de limite e a atividade.</span><span class="sxs-lookup"><span data-stu-id="357c6-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="357c6-104">Você também pode analisar [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos a partir de <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="357c6-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="357c6-105">A tabela a seguir lista os mais importantes.</span><span class="sxs-lookup"><span data-stu-id="357c6-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="357c6-106">Tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="357c6-106">Trace Type</span></span>|<span data-ttu-id="357c6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="357c6-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="357c6-108">Crítico</span><span class="sxs-lookup"><span data-stu-id="357c6-108">Critical</span></span>|<span data-ttu-id="357c6-109">Erro fatal ou falha do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="357c6-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="357c6-110">Erro</span><span class="sxs-lookup"><span data-stu-id="357c6-110">Error</span></span>|<span data-ttu-id="357c6-111">Erro recuperável.</span><span class="sxs-lookup"><span data-stu-id="357c6-111">Recoverable error.</span></span>|  
|<span data-ttu-id="357c6-112">Aviso</span><span class="sxs-lookup"><span data-stu-id="357c6-112">Warning</span></span>|<span data-ttu-id="357c6-113">Mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="357c6-113">Informational message.</span></span>|  
|<span data-ttu-id="357c6-114">Informações</span><span class="sxs-lookup"><span data-stu-id="357c6-114">Information</span></span>|<span data-ttu-id="357c6-115">Problema não crítico.</span><span class="sxs-lookup"><span data-stu-id="357c6-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="357c6-116">Detalhado</span><span class="sxs-lookup"><span data-stu-id="357c6-116">Verbose</span></span>|<span data-ttu-id="357c6-117">Rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="357c6-117">Debugging trace.</span></span>|  
|<span data-ttu-id="357c6-118">Início</span><span class="sxs-lookup"><span data-stu-id="357c6-118">Start</span></span>|<span data-ttu-id="357c6-119">Início de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="357c6-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="357c6-120">Suspender</span><span class="sxs-lookup"><span data-stu-id="357c6-120">Suspend</span></span>|<span data-ttu-id="357c6-121">Suspensão de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="357c6-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="357c6-122">Resume</span><span class="sxs-lookup"><span data-stu-id="357c6-122">Resume</span></span>|<span data-ttu-id="357c6-123">Continuação de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="357c6-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="357c6-124">Stop</span><span class="sxs-lookup"><span data-stu-id="357c6-124">Stop</span></span>|<span data-ttu-id="357c6-125">Interrupção de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="357c6-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="357c6-126">Transferir</span><span class="sxs-lookup"><span data-stu-id="357c6-126">Transfer</span></span>|<span data-ttu-id="357c6-127">Alteração da identidade de correlação.</span><span class="sxs-lookup"><span data-stu-id="357c6-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="357c6-128">Uma atividade é definida como uma combinação de tipos de rastreamento acima.</span><span class="sxs-lookup"><span data-stu-id="357c6-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="357c6-129">O exemplo a seguir é uma expressão regular que define uma atividade ideal em um escopo local (origem do rastreamento),</span><span class="sxs-lookup"><span data-stu-id="357c6-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="357c6-130">Isso significa que uma atividade deve satisfazer as condições a seguir.</span><span class="sxs-lookup"><span data-stu-id="357c6-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="357c6-131">Ele deve iniciar e parar respectivamente, um iniciar e parar rastreamentos</span><span class="sxs-lookup"><span data-stu-id="357c6-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="357c6-132">Ele deve ter um rastreamento de transferência imediatamente anteriores a um rastreamento de suspensão ou retomada</span><span class="sxs-lookup"><span data-stu-id="357c6-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="357c6-133">Ele não deve ter qualquer rastreamentos entre os rastreamentos de suspender e retomar se existirem rastreamentos</span><span class="sxs-lookup"><span data-stu-id="357c6-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="357c6-134">Ele pode ter qualquer e a quantidade de crítico/erro/aviso/informação/detalhado/transferência rastreamentos, desde que as condições anteriores são observadas</span><span class="sxs-lookup"><span data-stu-id="357c6-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="357c6-135">O exemplo a seguir é uma expressão regular que define uma atividade ideal no escopo global,</span><span class="sxs-lookup"><span data-stu-id="357c6-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="357c6-136">com R sendo a expressão regular para uma atividade no escopo local.</span><span class="sxs-lookup"><span data-stu-id="357c6-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="357c6-137">Isso se traduz em,</span><span class="sxs-lookup"><span data-stu-id="357c6-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
