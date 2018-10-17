---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 2371c38aebe2bd8d6da93d702801556fad986ef9
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372194"
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement
TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe TextMessageEncodingBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe TextMessageEncodingBindingElement tem as seguintes propriedades:  
  
### <a name="encoding"></a>Codificando  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.  
  
### <a name="maxreadpoolsize"></a>maxReadPoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.  
  
### <a name="maxwritepoolsize"></a>maxWritePoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.  
  
### <a name="readerquotas"></a>readerQuotas  
 Tipo de dados: XmlDictionaryReaderQuotas  
  
 Tipo de acesso: somente leitura  
  
 As cotas dos leitores.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
