---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: fdaf30e78b1a74a733753542acd6a41f15f176bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194820"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe PrivacyNoticeBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe PrivacyNoticeBindingElement tem as seguintes propriedades:  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A versão do aviso de privacidade.  
  
### <a name="url"></a>Url  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 A URL na qual o aviso de privacidade está localizado.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
