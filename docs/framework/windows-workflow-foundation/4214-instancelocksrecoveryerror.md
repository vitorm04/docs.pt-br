---
title: 4214 - InstanceLocksRecoveryError
ms.date: 03/30/2017
ms.assetid: d28fb2d5-bf15-4648-8d20-8141ad16f04b
ms.openlocfilehash: 247b105cf4e5a9d5c3c4b4d36a282763044658a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774098"
---
# <a name="4214---instancelocksrecoveryerror"></a>4214 - InstanceLocksRecoveryError
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|4214|  
|Palavras-chave|WFInstanceStore|  
|Nível|Erro|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Recuperando os bloqueios de instância falhados devido a uma exceção.  
  
## <a name="message"></a>Mensagem  
 Falha na recuperação dos bloqueios de instância devido à seguinte exceção  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Exceção|xs:string|Os detalhes de exceção para a exceção|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
