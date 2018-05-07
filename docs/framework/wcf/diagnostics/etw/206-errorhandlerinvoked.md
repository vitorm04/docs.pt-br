---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="206---errorhandlerinvoked"></a>206 - ErrorHandlerInvoked
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|206|  
|Palavras-chave|Solução de problemas, ServiceModel|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido após um `ErrorHandler` teve a oportunidade de manipular uma exceção que ocorreu em uma operação de serviço.  
  
## <a name="message"></a>Mensagem  
 O Dispatcher invocou um ErrorHandler do tipo '%1' com uma exceção do tipo '%3'. ErrorHandled = = '%2'.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|NomeDoTipo|`xs:string`|O FullName do CLR do tipo de chamada `ErrorHandler`.|  
|Tratado|`xs:unsignedByte`|`true` Se o manipulador de erro tratadas o erro, caso contrário, `false`.|  
|ExceptionTypeName|`xs:string`|O FullName do CLR da exceção que estava sendo tratada.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
