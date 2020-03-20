---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674834"
---
# <a name="trace-type-summary"></a><span data-ttu-id="d4773-102">Resumo de tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="d4773-102">Trace Type Summary</span></span>
<span data-ttu-id="d4773-103">[Os Níveis de Origem](xref:System.Diagnostics.SourceLevels) definem vários níveis de rastreamento: Crítico, Erro, Aviso, `ActivityTracing` Informação e Verbose, bem como fornece uma descrição do sinalizador, que alterna a saída de eventos de limite de rastreamento e transferência de atividade.</span><span class="sxs-lookup"><span data-stu-id="d4773-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="d4773-104">Você também <xref:System.Diagnostics.TraceEventType> pode revisar os tipos de traços <xref:System.Diagnostics>que podem ser emitidos a partir de .</span><span class="sxs-lookup"><span data-stu-id="d4773-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="d4773-105">A tabela a seguir lista as mais importantes.</span><span class="sxs-lookup"><span data-stu-id="d4773-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="d4773-106">Tipo de traço</span><span class="sxs-lookup"><span data-stu-id="d4773-106">Trace Type</span></span>|<span data-ttu-id="d4773-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d4773-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="d4773-108">Crítico</span><span class="sxs-lookup"><span data-stu-id="d4773-108">Critical</span></span>|<span data-ttu-id="d4773-109">Erro fatal ou falha do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4773-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="d4773-110">Erro</span><span class="sxs-lookup"><span data-stu-id="d4773-110">Error</span></span>|<span data-ttu-id="d4773-111">Erro recuperável.</span><span class="sxs-lookup"><span data-stu-id="d4773-111">Recoverable error.</span></span>|  
|<span data-ttu-id="d4773-112">Aviso</span><span class="sxs-lookup"><span data-stu-id="d4773-112">Warning</span></span>|<span data-ttu-id="d4773-113">Mensagem informativa.</span><span class="sxs-lookup"><span data-stu-id="d4773-113">Informational message.</span></span>|  
|<span data-ttu-id="d4773-114">Informações</span><span class="sxs-lookup"><span data-stu-id="d4773-114">Information</span></span>|<span data-ttu-id="d4773-115">Problema não crítico.</span><span class="sxs-lookup"><span data-stu-id="d4773-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="d4773-116">Detalhado</span><span class="sxs-lookup"><span data-stu-id="d4773-116">Verbose</span></span>|<span data-ttu-id="d4773-117">Rastreamento de depuração.</span><span class="sxs-lookup"><span data-stu-id="d4773-117">Debugging trace.</span></span>|  
|<span data-ttu-id="d4773-118">Iniciar</span><span class="sxs-lookup"><span data-stu-id="d4773-118">Start</span></span>|<span data-ttu-id="d4773-119">Começando uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="d4773-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="d4773-120">Suspend</span><span class="sxs-lookup"><span data-stu-id="d4773-120">Suspend</span></span>|<span data-ttu-id="d4773-121">Suspensão de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="d4773-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="d4773-122">Continuar</span><span class="sxs-lookup"><span data-stu-id="d4773-122">Resume</span></span>|<span data-ttu-id="d4773-123">Retomada de uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="d4773-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="d4773-124">Stop</span><span class="sxs-lookup"><span data-stu-id="d4773-124">Stop</span></span>|<span data-ttu-id="d4773-125">Parando uma unidade lógica de processamento.</span><span class="sxs-lookup"><span data-stu-id="d4773-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="d4773-126">Transferir</span><span class="sxs-lookup"><span data-stu-id="d4773-126">Transfer</span></span>|<span data-ttu-id="d4773-127">Alteração da identidade de correlação.</span><span class="sxs-lookup"><span data-stu-id="d4773-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="d4773-128">Uma atividade é definida como uma combinação dos tipos de traçoacima.</span><span class="sxs-lookup"><span data-stu-id="d4773-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="d4773-129">A seguir é uma expressão regular que define uma atividade ideal em um escopo local (fonte de rastreamento),</span><span class="sxs-lookup"><span data-stu-id="d4773-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="d4773-130">Isso significa que uma atividade deve satisfazer as seguintes condições.</span><span class="sxs-lookup"><span data-stu-id="d4773-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="d4773-131">Ele deve começar e parar, respectivamente, por um rastreamento start e stop</span><span class="sxs-lookup"><span data-stu-id="d4773-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="d4773-132">Ele deve ter um rastreamento de transferência imediatamente antes de um rastreamento suspender ou retomar</span><span class="sxs-lookup"><span data-stu-id="d4773-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="d4773-133">Ele não deve ter quaisquer vestígios entre os traços Suspender e Retomar se tais vestígios existem</span><span class="sxs-lookup"><span data-stu-id="d4773-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="d4773-134">Ele pode ter qualquer e tantos de traços críticos/erro/aviso/informações/verbose/transferência, desde que as condições anteriores sejam observadas</span><span class="sxs-lookup"><span data-stu-id="d4773-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="d4773-135">A seguir é uma expressão regular que define uma atividade ideal no âmbito global,</span><span class="sxs-lookup"><span data-stu-id="d4773-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="d4773-136">com R sendo a expressão regular para uma atividade no escopo local.</span><span class="sxs-lookup"><span data-stu-id="d4773-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="d4773-137">Isso se traduz em,</span><span class="sxs-lookup"><span data-stu-id="d4773-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
