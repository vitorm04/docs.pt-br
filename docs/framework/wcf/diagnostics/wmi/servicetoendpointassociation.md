---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048225"
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
 Tipo de dados: Serviço  
  
 Tipo de acesso: Somente leitura  
Qualificadores: Chave  
  
 O serviço associado com o ponto de extremidade.  
  
### <a name="ref"></a>ref  
 Tipo de dados: Ponto de extremidade  
  
 Tipo de acesso: Somente leitura  
Qualificadores: Chave  
  
 O ponto de extremidade associado ao serviço.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|
