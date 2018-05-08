---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e3bc66753dd44e1dc4c7417caf593820300f69a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="trace-type-summary"></a>Resumo de tipo de rastreamento
[Níveis de origem](http://go.microsoft.com/fwlink/?LinkID=94943) define vários níveis de rastreamento: crítico, erro, aviso, informações e detalhado, bem como fornece descrição do `ActivityTracing` sinalizador, que alterna a saída de rastreamento de eventos de transferência de limite e a atividade.  
  
 Você também pode analisar [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos a partir de <xref:System.Diagnostics>.  
  
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
|Stop|Interrupção de uma unidade lógica de processamento.|  
|Transferir|Alteração da identidade de correlação.|  
  
 Uma atividade é definida como uma combinação de tipos de rastreamento acima.  
  
 O exemplo a seguir é uma expressão regular que define uma atividade ideal em um escopo local (origem do rastreamento),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Isso significa que uma atividade deve satisfazer as condições a seguir.  
  
-   Ele deve iniciar e parar respectivamente, um iniciar e parar rastreamentos  
  
-   Ele deve ter um rastreamento de transferência imediatamente anteriores a um rastreamento de suspensão ou retomada  
  
-   Ele não deve ter qualquer rastreamentos entre os rastreamentos de suspender e retomar se existirem rastreamentos  
  
-   Ele pode ter qualquer e a quantidade de crítico/erro/aviso/informação/detalhado/transferência rastreamentos, desde que as condições anteriores são observadas  
  
 O exemplo a seguir é uma expressão regular que define uma atividade ideal no escopo global,  
  
```  
R+   
```  
  
 com R sendo a expressão regular para uma atividade no escopo local. Isso se traduz em,  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
