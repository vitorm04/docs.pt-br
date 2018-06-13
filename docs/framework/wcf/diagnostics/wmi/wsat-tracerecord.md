---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487770"
---
# <a name="wsattracerecord"></a><span data-ttu-id="c059d-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="c059d-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="c059d-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="c059d-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c059d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c059d-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c059d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c059d-105">Methods</span></span>  
 <span data-ttu-id="c059d-106">A classe WSAT_TraceRecord não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c059d-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c059d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c059d-107">Properties</span></span>  
 <span data-ttu-id="c059d-108">A classe WSAT_TraceRecord tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c059d-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="c059d-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="c059d-109">ActivityID</span></span>  
 <span data-ttu-id="c059d-110">Tipo de dados: objeto</span><span class="sxs-lookup"><span data-stu-id="c059d-110">Data type: object</span></span>  
<span data-ttu-id="c059d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c059d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c059d-112">A ID de atividade do registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c059d-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="c059d-113">EventID</span><span class="sxs-lookup"><span data-stu-id="c059d-113">EventID</span></span>  
 <span data-ttu-id="c059d-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c059d-114">Data type: sint32</span></span>  
<span data-ttu-id="c059d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c059d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c059d-116">A ID de evento do registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c059d-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="c059d-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="c059d-117">TraceRecord</span></span>  
 <span data-ttu-id="c059d-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c059d-118">Data type: string</span></span>  
<span data-ttu-id="c059d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c059d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c059d-120">Registro de rastreamento</span><span class="sxs-lookup"><span data-stu-id="c059d-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c059d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c059d-121">Requirements</span></span>  
  
|<span data-ttu-id="c059d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c059d-122">MOF</span></span>|<span data-ttu-id="c059d-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c059d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c059d-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="c059d-124">Namespace</span></span>|<span data-ttu-id="c059d-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c059d-125">Defined in root\ServiceModel</span></span>|
