---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="05fe9-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="05fe9-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="05fe9-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="05fe9-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05fe9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05fe9-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="05fe9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="05fe9-105">Methods</span></span>  
 <span data-ttu-id="05fe9-106">A classe WSAT_TraceRecord não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="05fe9-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="05fe9-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="05fe9-107">Properties</span></span>  
 <span data-ttu-id="05fe9-108">A classe WSAT_TraceRecord tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="05fe9-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="05fe9-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="05fe9-109">ActivityID</span></span>  
 <span data-ttu-id="05fe9-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="05fe9-110">Data type: object</span></span>  
<span data-ttu-id="05fe9-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="05fe9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05fe9-112">A ID de atividade do registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="05fe9-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="05fe9-113">EventID</span><span class="sxs-lookup"><span data-stu-id="05fe9-113">EventID</span></span>  
 <span data-ttu-id="05fe9-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="05fe9-114">Data type: sint32</span></span>  
<span data-ttu-id="05fe9-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="05fe9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05fe9-116">A ID de evento do registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="05fe9-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="05fe9-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="05fe9-117">TraceRecord</span></span>  
 <span data-ttu-id="05fe9-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="05fe9-118">Data type: string</span></span>  
<span data-ttu-id="05fe9-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="05fe9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05fe9-120">Registro de rastreamento</span><span class="sxs-lookup"><span data-stu-id="05fe9-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05fe9-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05fe9-121">Requirements</span></span>  
  
|<span data-ttu-id="05fe9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="05fe9-122">MOF</span></span>|<span data-ttu-id="05fe9-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="05fe9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="05fe9-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="05fe9-124">Namespace</span></span>|<span data-ttu-id="05fe9-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="05fe9-125">Defined in root\ServiceModel</span></span>|
