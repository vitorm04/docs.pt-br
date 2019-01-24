---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 330496d5f0f80affcb6bc44a1f66f4321a635f00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580584"
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe BinaryMessageEncodingBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.  
  
## <a name="maxsessionsize"></a>MaxSessionSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.  
  
## <a name="readerquotas"></a>ReaderQuotas  
 Tipo de dados: XmlDictionaryReaderQuotas  
  
 Tipo de acesso: Somente leitura  
  
 As cotas dos leitores.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
