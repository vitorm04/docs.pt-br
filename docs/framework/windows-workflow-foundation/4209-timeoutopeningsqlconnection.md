---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774264"
---
# <a name="4209---timeoutopeningsqlconnection"></a>4209 - TimeoutOpeningSqlConnection
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|4209|  
|Palavras-chave|WFInstanceStore|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um tempo limite foi encontrado ao tentar abrir uma conexão SQL.  
  
## <a name="message"></a>Mensagem  
 O tempo limite está tentando abrir uma conexão de SQL. A operação não concluiu dentro do tempo limite distribuído de %1. O tempo determinado para essa operação pode ter sido uma parte de um tempo limite maior.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Tempo limite|xs:string|O valor de tempo limite para abrir a conexão SQL.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
