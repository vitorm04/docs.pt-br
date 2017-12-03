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
