---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: b1e5b87b053e947432cba9f6e716f7d1ea8f013f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
