---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372159"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Mapeia um serviço para um ponto de extremidade.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceToEndpointAssociation não define quaisquer métodos.  
  
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
|Namespace|Definido no root\ServiceModel|
