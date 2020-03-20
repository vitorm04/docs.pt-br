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
# <a name="trace-type-summary"></a>Resumo de tipo de rastreamento
[Os Níveis de Origem](xref:System.Diagnostics.SourceLevels) definem vários níveis de rastreamento: Crítico, Erro, Aviso, `ActivityTracing` Informação e Verbose, bem como fornece uma descrição do sinalizador, que alterna a saída de eventos de limite de rastreamento e transferência de atividade.  
  
 Você também <xref:System.Diagnostics.TraceEventType> pode revisar os tipos de traços <xref:System.Diagnostics>que podem ser emitidos a partir de .  
  
 A tabela a seguir lista as mais importantes.  
  
|Tipo de traço|Descrição|  
|----------------|-----------------|  
|Crítico|Erro fatal ou falha do aplicativo.|  
|Erro|Erro recuperável.|  
|Aviso|Mensagem informativa.|  
|Informações|Problema não crítico.|  
|Detalhado|Rastreamento de depuração.|  
|Iniciar|Começando uma unidade lógica de processamento.|  
|Suspend|Suspensão de uma unidade lógica de processamento.|  
|Continuar|Retomada de uma unidade lógica de processamento.|  
|Stop|Parando uma unidade lógica de processamento.|  
|Transferir|Alteração da identidade de correlação.|  
  
 Uma atividade é definida como uma combinação dos tipos de traçoacima.  
  
 A seguir é uma expressão regular que define uma atividade ideal em um escopo local (fonte de rastreamento),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Isso significa que uma atividade deve satisfazer as seguintes condições.  
  
- Ele deve começar e parar, respectivamente, por um rastreamento start e stop  
  
- Ele deve ter um rastreamento de transferência imediatamente antes de um rastreamento suspender ou retomar  
  
- Ele não deve ter quaisquer vestígios entre os traços Suspender e Retomar se tais vestígios existem  
  
- Ele pode ter qualquer e tantos de traços críticos/erro/aviso/informações/verbose/transferência, desde que as condições anteriores sejam observadas  
  
 A seguir é uma expressão regular que define uma atividade ideal no âmbito global,  
  
`R+`  
  
 com R sendo a expressão regular para uma atividade no escopo local. Isso se traduz em,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
