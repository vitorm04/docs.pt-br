---
title: ServiceToEndpointAssociation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da8703b80f2fbcc2f02eb64c94baf0707a1a93bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Um serviço é mapeado para um ponto de extremidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceToEndpointAssociation não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceToEndpointAssociation tem as seguintes propriedades:  
  
### <a name="ref"></a>ref  
 Tipo de dados: serviço  
  
 Tipo de acesso: somente leitura  
Qualificadores: chave  
  
 O serviço associado com o ponto de extremidade.  
  
### <a name="ref"></a>ref  
 Tipo de dados: ponto de extremidade  
  
 Tipo de acesso: somente leitura  
Qualificadores: chave  
  
 O ponto de extremidade associado ao serviço.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|
