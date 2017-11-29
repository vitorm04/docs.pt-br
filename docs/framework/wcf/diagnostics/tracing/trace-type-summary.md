---
title: Resumo de tipo de rastreamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8e82f153e996ffebc2aba614f42c5cfa949e7ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="trace-type-summary"></a><span data-ttu-id="4448d-102">Resumo de tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="4448d-102">Trace Type Summary</span></span>
<span data-ttu-id="4448d-103">[Níveis de origem](http://go.microsoft.com/fwlink/?LinkID=94943) define vários níveis de rastreamento: crítico, erro, aviso, informações e detalhado, bem como fornece descrição do `ActivityTracing` sinalizador, que alterna a saída de rastreamento de eventos de transferência de limite e a atividade.</span><span class="sxs-lookup"><span data-stu-id="4448d-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="4448d-104">Você também pode analisar [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos a partir de <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="4448d-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="4448d-105">A tabela a seguir lista os mais importantes.</span><span class="sxs-lookup"><span data-stu-id="4448d-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="4448d-106">Tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="4448d-106">Trace Type</span></span>|<span data-ttu-id="4448d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4448d-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="4448d-108">Crítico</span><span class="sxs-lookup"><span data-stu-id="4448d-108">Critical</span></span>|<span data-ttu-id="4448d-109">Erro fatal ou falha do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4448d-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="4448d-110">Erro</span><span class="sxs-lookup"><span data-stu-id="4448d-110">Error</span></span>|<span data-ttu-id="4448d-111">Erro recuperável.</span><span class="sxs-lookup"><span data-stu-id="4448d-111">Recoverable error.</span></span>|  
|<span data-ttu-id="4448d-112">Aviso</span><span class="sxs-lookup"><span data-stu-id="4448d-112">Warning</span></span>|<span data-ttu-id="4448d-113">Mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="4448d-113">Informational message.</span></span>|  
|<span data-ttu-id="4448d-114">Informações</span><span class="sxs-lookup"><span data-stu-id="4448d-114">Information</span></span>|<span data-ttu-id="4448d-115">Problema não crítico.</span><span class="sxs-lookup"><span data-stu-id="4448d-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="4448d-116">Detalhado</span><span class="sxs-lookup"><span data-stu-id="4448d-116">Verbose</span></span>|<span data-ttu-id="4448d-117">Rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="4448d-117">Debugging trace.</span></span>|  
|<span data-ttu-id="4448d-118">Início</span><span class="sxs-lookup"><span data-stu-id="4448d-118">Start</span></span>|<span data-ttu-id="4448d-119">Início de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="4448d-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4448d-120">Suspender</span><span class="sxs-lookup"><span data-stu-id="4448d-120">Suspend</span></span>|<span data-ttu-id="4448d-121">Suspensão de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="4448d-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4448d-122">Resume</span><span class="sxs-lookup"><span data-stu-id="4448d-122">Resume</span></span>|<span data-ttu-id="4448d-123">Continuação de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="4448d-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4448d-124">Stop</span><span class="sxs-lookup"><span data-stu-id="4448d-124">Stop</span></span>|<span data-ttu-id="4448d-125">Interrupção de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="4448d-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="4448d-126">Transferir</span><span class="sxs-lookup"><span data-stu-id="4448d-126">Transfer</span></span>|<span data-ttu-id="4448d-127">Alteração da identidade de correlação.</span><span class="sxs-lookup"><span data-stu-id="4448d-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="4448d-128">Uma atividade é definida como uma combinação de tipos de rastreamento acima.</span><span class="sxs-lookup"><span data-stu-id="4448d-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="4448d-129">O exemplo a seguir é uma expressão regular que define uma atividade ideal em um escopo local (origem do rastreamento),</span><span class="sxs-lookup"><span data-stu-id="4448d-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="4448d-130">Isso significa que uma atividade deve satisfazer as condições a seguir.</span><span class="sxs-lookup"><span data-stu-id="4448d-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="4448d-131">Ele deve iniciar e parar respectivamente, um iniciar e parar rastreamentos</span><span class="sxs-lookup"><span data-stu-id="4448d-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="4448d-132">Ele deve ter um rastreamento de transferência imediatamente anteriores a um rastreamento de suspensão ou retomada</span><span class="sxs-lookup"><span data-stu-id="4448d-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="4448d-133">Ele não deve ter qualquer rastreamentos entre os rastreamentos de suspender e retomar se existirem rastreamentos</span><span class="sxs-lookup"><span data-stu-id="4448d-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="4448d-134">Ele pode ter qualquer e a quantidade de crítico/erro/aviso/informação/detalhado/transferência rastreamentos, desde que as condições anteriores são observadas</span><span class="sxs-lookup"><span data-stu-id="4448d-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="4448d-135">O exemplo a seguir é uma expressão regular que define uma atividade ideal no escopo global,</span><span class="sxs-lookup"><span data-stu-id="4448d-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="4448d-136">com R sendo a expressão regular para uma atividade no escopo local.</span><span class="sxs-lookup"><span data-stu-id="4448d-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="4448d-137">Isso se traduz em,</span><span class="sxs-lookup"><span data-stu-id="4448d-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
