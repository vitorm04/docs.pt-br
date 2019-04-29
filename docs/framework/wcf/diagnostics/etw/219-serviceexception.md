---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781726"
---
# <a name="219---serviceexception"></a>219 - ServiceException
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|219|  
|Palavras-chave|EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento é emitido quando um serviço WCF encontra uma exceção sem tratamento. Isso inclui exceções sem tratamento durante a ativação, durante o processamento da mensagem e no código do usuário.  
  
## <a name="message"></a>Mensagem  
 Houve uma exceção sem tratamento do tipo '%2' durante o processamento da mensagem. ToString completo da exceção: %1.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|O resultado da chamada `ToString`() em que a exceção do CLR.|  
|ExceptionTypeName|`xs:string`|O FullName do CLR do tipo da exceção.|  
|HostReference|`xs:string`|Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web. O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'. Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
