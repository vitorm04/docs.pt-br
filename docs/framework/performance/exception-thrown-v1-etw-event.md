---
title: Evento ETW Exception Thrown_V1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dcf3390821c4210ced4c43dab5a94c93802d5f9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-thrownv1-etw-event"></a>Evento ETW Exception Thrown_V1
Esse evento captura informações sobre as exceções geradas.  
  
 A tabela a seguir mostra a palavra-chave com a qual o evento é acionado, além do nível do evento. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Aviso (2)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|Evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Uma exceção gerenciada é gerada.|  
  
 A tabela a seguir mostra dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|Tipo de exceção|win:UnicodeString|Tipo da exceção; por exemplo, `System.NullReferenceException`.|  
|Mensagem de exceção|win:UnicodeString|A mensagem de exceção real.|  
|EIPCodeThrow|win:Pointer|Ponteiro de instrução em que ocorreu a exceção.|  
|ExceptionHR|win:UInt32|Exceção [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|win:UInt16|0x01: HasInnerException (consulte [Eventos CLR ETW](../../../docs/framework/performance/clr-etw-events.md) na documentação do Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (indica que o estado do processo está corrompido; consulte [Tratando exceções de estado corrompido](http://go.microsoft.com/fwlink/?LinkId=179681) no MSDN).<br /><br /> 0x10: IsCLSCompliant (uma exceção que é derivada de <xref:System.Exception> está em conformidade com CLS; caso contrário, ela não está em conformidade com CLS).|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
## <a name="see-also"></a>Consulte também  
 [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
