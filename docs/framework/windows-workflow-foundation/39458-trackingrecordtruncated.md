---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|39458|  
|Palavras-chave|WFTracking|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um registro de rastreamento foi truncado. Variáveis/anotações/dados do usuário serem removidos.  
  
## <a name="message"></a>Mensagem  
 Registro truncado %1 de rastreamento gravados para a sessão de ETW com provedor %2. Dados de variáveis/anotações/usuários foram removidos  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|O número de registro controlando.|  
|ProviderId|xs:string|A identificação do provedor de ETW|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
