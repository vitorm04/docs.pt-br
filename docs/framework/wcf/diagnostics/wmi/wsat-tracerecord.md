---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923403"
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe WSAT_TraceRecord não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe WSAT_TraceRecord tem as seguintes propriedades:  
  
### <a name="activityid"></a>ActivityID  
 Tipo de dados: objeto  
Tipo de acesso: Somente leitura  
  
 A ID de atividade de registro de rastreamento.  
  
### <a name="eventid"></a>EventID  
 Tipo de dados: sint32  
Tipo de acesso: Somente leitura  
  
 A ID do evento de registro de rastreamento.  
  
### <a name="tracerecord"></a>TraceRecord  
 Tipo de dados: cadeia de caracteres  
Tipo de acesso: Somente leitura  
  
 Registro de rastreamento  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|
