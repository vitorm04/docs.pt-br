---
title: Eventos ETW de interoperabilidade
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38db390b8fad9cd36dacf33f9647b0272eddc4a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616417"
---
# <a name="interop-etw-events"></a>Eventos ETW de interoperabilidade
<a name="top"></a> Eventos de interoperabilidade capturam informações sobre a geração e o cache de stub da MSIL (Microsoft Intermediate Language).  
  
 Esta categoria consiste nos seguintes eventos:  
  
- [Evento ILStubGenerated](#ilstubgenerated_event)  
  
- [Evento ILStubCacheHit](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>Evento ILStubGenerated  
 A tabela a seguir mostra a palavra-chave e o nível. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|O stub em MSIL foi gerado.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|O identificador de módulo.|  
|StubMethodID|win:UInt64|O identificador do método de stub.|  
|StubFlags|win:UInt64|Os sinalizadores para o stub:<br /><br /> 0x1 – interoperabilidade revesa.<br /><br /> 0x2 – interoperabilidade COM.<br /><br /> 0x4 – stub gerado pelo NGen.exe.<br /><br /> 0x8 – delegado.<br /><br /> 0x10 – argumento variável.<br /><br /> 0x20 – receptor não gerenciado.|  
|ManagedInteropMethodToken|win:UInt32|O token para o método de interoperabilidade gerenciado.|  
|ManagedInteropMethodNameSpace|win:UnicodeString|O namespace do método de interoperabilidade gerenciado.|  
|ManagedInteropMethodName|win:UnicodeString|O nome do método de interoperabilidade gerenciado.|  
|ManagedInteropMethodSignature|win:UnicodeString|A assinatura do método de interoperabilidade gerenciado.|  
|NativeMethodSignature|win:UnicodeString|A assinatura do método nativo.|  
|StubMethodSignature|win:UnicodeString|A assinatura do método de stub.|  
|StubMethodILCode|win:UnicodeString|O código MSIL para o método de stub.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>Evento ILStubCacheHit  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|O cache MSIL foi acessado.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt16|O identificador de módulo.|  
|StubMethodID|win:UInt64|O identificador do método de stub.|  
|ManagedInteropMethodToken|win:UInt32|O token para o método de interoperabilidade gerenciado.|  
|ManagedInteropMethodNameSpace|win:UnicodeString|O namespace do método de interoperabilidade gerenciado.|  
|ManagedInteropMethodName|win:UnicodeString|O nome do método de interoperabilidade gerenciado.|  
|ManagedInteropMethodSignature|win:UnicodeString|A assinatura do método de interoperabilidade gerenciado.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
 [Voltar ao início](#top)  
  
## <a name="see-also"></a>Consulte também

- [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
