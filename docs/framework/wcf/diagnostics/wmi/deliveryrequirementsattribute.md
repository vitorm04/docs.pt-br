---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe DeliveryRequirementsAttribute não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe DeliveryRequirementsAttribute tem as seguintes propriedades:  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Especifica se a associação para um serviço oferece suporte a contratos.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Especifica se a associação oferece suporte a mensagens ordenadas.  
  
### <a name="targetcontract"></a>TargetContract  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O contrato ao qual se aplica.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
