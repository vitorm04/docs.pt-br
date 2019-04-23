---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: 04c65d0aa589d99766b4ffc8f1550036d2880718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976372"
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
  
 Tipo de acesso: Somente leitura  
  
 A versão do aviso de privacidade.  
  
### <a name="url"></a>Url  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 A URL na qual o aviso de privacidade está localizado.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
