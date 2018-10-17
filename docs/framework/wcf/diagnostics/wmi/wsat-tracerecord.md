---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49373990"
---
# <a name="wsattracerecord"></a><span data-ttu-id="13d6e-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="13d6e-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="13d6e-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="13d6e-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d6e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13d6e-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="13d6e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="13d6e-105">Methods</span></span>  
 <span data-ttu-id="13d6e-106">A classe WSAT_TraceRecord não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="13d6e-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="13d6e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="13d6e-107">Properties</span></span>  
 <span data-ttu-id="13d6e-108">A classe WSAT_TraceRecord tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="13d6e-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="13d6e-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="13d6e-109">ActivityID</span></span>  
 <span data-ttu-id="13d6e-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="13d6e-110">Data type: object</span></span>  
<span data-ttu-id="13d6e-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="13d6e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13d6e-112">A ID de atividade de registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="13d6e-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="13d6e-113">EventID</span><span class="sxs-lookup"><span data-stu-id="13d6e-113">EventID</span></span>  
 <span data-ttu-id="13d6e-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="13d6e-114">Data type: sint32</span></span>  
<span data-ttu-id="13d6e-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="13d6e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13d6e-116">A ID do evento de registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="13d6e-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="13d6e-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="13d6e-117">TraceRecord</span></span>  
 <span data-ttu-id="13d6e-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="13d6e-118">Data type: string</span></span>  
<span data-ttu-id="13d6e-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="13d6e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="13d6e-120">Registro de rastreamento</span><span class="sxs-lookup"><span data-stu-id="13d6e-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d6e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13d6e-121">Requirements</span></span>  
  
|<span data-ttu-id="13d6e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="13d6e-122">MOF</span></span>|<span data-ttu-id="13d6e-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="13d6e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="13d6e-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="13d6e-124">Namespace</span></span>|<span data-ttu-id="13d6e-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="13d6e-125">Defined in root\ServiceModel</span></span>|
