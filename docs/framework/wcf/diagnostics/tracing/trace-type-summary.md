---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 44446b58510e58758934a5eb964efc8643854879
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647181"
---
# <a name="trace-type-summary"></a>Resumo de tipo de rastreamento
[Níveis de origem](https://go.microsoft.com/fwlink/?LinkID=94943) define vários níveis de rastreamento: Crítico, erro, aviso, informações e detalhado, bem como fornece a descrição do `ActivityTracing` sinalizador, que alterna a saída de rastreamento de eventos de transferência de limite e a atividade.  
  
 Você também pode examinar [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos de <xref:System.Diagnostics>.  
  
 A tabela a seguir lista os mais importantes.  
  
|Tipo de rastreamento|Descrição|  
|----------------|-----------------|  
|Crítico|Erro fatal ou falha do aplicativo.|  
|Erro|Erro recuperável.|  
|Aviso|Mensagem informativa.|  
|Informações|Problema não crítico.|  
|Detalhado|Rastreamento de depuração.|  
|Início|Início de uma unidade lógica de processamento.|  
|Suspender|Suspensão de uma unidade lógica de processamento.|  
|Resume|Continuação de uma unidade lógica de processamento.|  
|Stop|Parada de uma unidade lógica de processamento.|  
|Transferir|Alteração da identidade de correlação.|  
  
 Uma atividade é definida como uma combinação dos tipos de rastreamento acima.  
  
 O exemplo a seguir é uma expressão regular que define uma atividade ideal em um escopo local (origem de rastreamento),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Isso significa que uma atividade deve satisfazer as condições a seguir.  
  
- Ele deve iniciar e parar, respectivamente, rastreamentos de início e parada  
  
- Ele deve ter um rastreamento de transferência imediatamente anterior a um rastreamento de suspensão ou retomada  
  
- Ele não deve ter os rastreamentos entre os rastreamentos de suspender e continuar se existirem tais rastreamentos  
  
- Ele pode ter qualquer e a quantidade de rastreamentos de crítico/erro/aviso / / detalhado/transferência de informações, desde que as condições anteriores forem observadas  
  
 O exemplo a seguir é uma expressão regular que define uma atividade ideal no escopo global,  
  
```  
R+   
```  
  
 com o R que é a expressão regular para uma atividade no escopo local. Isso se traduz em,  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
