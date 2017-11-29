---
title: 39457 - TrackingRecordRaised
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d2e142db5834a6c867970a28ec74e9fceebee16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
