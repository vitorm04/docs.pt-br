---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 67c1083daa9acfd204d4de50d4e9178b25aafcf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858384"
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
  
 Tipo de acesso: Somente leitura  
  
 O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.  
  
### <a name="readerquotas"></a>ReaderQuotas  
 Tipo de dados: XmlDictionaryReaderQuotas  
  
 Tipo de acesso: Somente leitura  
  
 As cotas dos leitores.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
