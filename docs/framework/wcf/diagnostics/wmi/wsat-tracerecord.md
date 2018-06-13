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
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe WSAT_TraceRecord não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe WSAT_TraceRecord tem as seguintes propriedades:  
  
### <a name="activityid"></a>ActivityID  
 Tipo de dados: objeto  
Tipo de acesso: somente leitura  
  
 A ID de atividade do registro de rastreamento.  
  
### <a name="eventid"></a>EventID  
 Tipo de dados: sint32  
Tipo de acesso: somente leitura  
  
 A ID de evento do registro de rastreamento.  
  
### <a name="tracerecord"></a>TraceRecord  
 Tipo de dados: cadeia de caracteres  
Tipo de acesso: somente leitura  
  
 Registro de rastreamento  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|
