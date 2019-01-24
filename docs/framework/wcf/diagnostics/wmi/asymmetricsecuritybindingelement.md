---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: e968f5f2d7ffdb193b30762d32a47be3778b98dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621351"
---
# <a name="asymmetricsecuritybindingelement"></a>AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe AsymmetricSecurityBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe AsymmetricSecurityBindingElement tem as seguintes propriedades:  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A ordem de criptografia de mensagens e a assinatura para esta associação.  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Se a associação requer confirmação de assinatura.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
