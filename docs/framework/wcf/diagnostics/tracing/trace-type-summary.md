---
title: Resumo de tipo de rastreamento
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856005"
---
# <a name="trace-type-summary"></a>Resumo de tipo de rastreamento
[Os níveis de origem](https://go.microsoft.com/fwlink/?LinkID=94943) definem vários níveis de rastreamento: Crítico, erro, aviso, informações e detalhado, bem como fornece a `ActivityTracing` descrição do sinalizador, que alterna a saída de eventos de limite de rastreamento e de transferência de atividade.  
  
 Você também pode examinar [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) para os tipos de rastreamentos que podem ser emitidos <xref:System.Diagnostics>.  
  
 A tabela a seguir lista os mais importantes.  
  
|Tipo de rastreamento|Descrição|  
|----------------|-----------------|  
|Crítica|Erro fatal ou falha do aplicativo.|  
|Erro|Erro recuperável.|  
|Aviso|Mensagem informativa.|  
|Informações|Problema não crítico.|  
|Detalhado|Rastreamento de depuração.|  
|Início|Início de uma unidade lógica de processamento.|  
|Suspend|Suspensão de uma unidade lógica de processamento.|  
|Continuar|Retomada de uma unidade lógica de processamento.|  
|Parar|Interrupção de uma unidade lógica de processamento.|  
|Transferir|Alteração da identidade de correlação.|  
  
 Uma atividade é definida como uma combinação dos tipos de rastreamento acima.  
  
 Veja a seguir uma expressão regular que define uma atividade ideal em um escopo local (origem do rastreamento),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Isso significa que uma atividade deve atender às condições a seguir.  
  
- Ele deve iniciar e parar respectivamente por um rastreamento de iniciar e parar  
  
- Ele deve ter um rastreamento de transferência imediatamente antes de um rastreamento de suspensão ou retomada  
  
- Ele não deve ter nenhum rastreamento entre os rastreamentos suspender e retomar se esses rastreamentos existirem  
  
- Ele pode ter qualquer e quantos rastreamentos crítico/erro/aviso/informações/detalhados/de transferência, desde que as condições anteriores sejam observadas  
  
 Veja a seguir uma expressão regular que define uma atividade ideal no escopo global,  
  
`R+`  
  
 o R é a expressão regular para uma atividade no escopo local. Isso se traduz em,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
