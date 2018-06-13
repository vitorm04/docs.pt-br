---
title: 3501 - InferredContractDescription
ms.date: 03/30/2017
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
ms.openlocfilehash: 47a5d98f4510e8c6092e8533a98366141d4b24db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512347"
---
# <a name="3501---inferredcontractdescription"></a>3501 - InferredContractDescription
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|3501|  
|Palavras-chave|WFServices|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Indica que um ContractDescription foi inferido de WorkflowService.  
  
## <a name="message"></a>Mensagem  
 ContractDescription com Name='%1 e Namespace='%2 foi inferido de WorkflowService.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome|xs:string|O nome de ContractDescription.|  
|Namespace|xs:string|O namespace de ContractDescription.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
