---
title: 2576 - TryCatchExceptionFromTry
ms.date: 03/30/2017
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
ms.openlocfilehash: cdc48a1a08e997f7bc6a0ad6b93aa13640af9ed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512688"
---
# <a name="2576---trycatchexceptionfromtry"></a>2576 - TryCatchExceptionFromTry
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|2576|  
|Palavras-chave|WFActivities|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que a atividade de TryCatch capturou uma exceção.  
  
## <a name="message"></a>Mensagem  
 A atividade “%1 " de TryCatch capturou uma exceção “%2 ".  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|O nome para exibição de atividade.|  
|Exceção|xs:string|O nome do tipo de exceção.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
