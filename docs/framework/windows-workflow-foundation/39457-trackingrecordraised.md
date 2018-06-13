---
title: 39457 - TrackingRecordRaised
ms.date: 03/30/2017
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
ms.openlocfilehash: 104d3fb4b544172001051be7bccc3721cf8d6d1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512360"
---
# <a name="39457---trackingrecordraised"></a>39457 - TrackingRecordRaised
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|39457|  
|Palavras-chave|WFRuntime|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um TrackingRecord foi gerado para um TrackingParticipant.  
  
## <a name="message"></a>Mensagem  
 Controlando o registro %1 elevado a %2.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|O número de registro controlando.|  
|ParticipantId|xs:string|O participante de rastreamento.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
