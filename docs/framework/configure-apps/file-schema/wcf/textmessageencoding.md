---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 640cf8fce766f7107e297143e061f4f60d9f263d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753476"
---
# <a name="lttextmessageencodinggt"></a>&lt;textMessageEncoding&gt;
Especifica a codificação de caracteres e a mensagem de controle de versão é usada para mensagens XML baseadas em texto.  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<textMessageEncoding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|maxReadPoolSize|Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores. Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho. O padrão é 64.|  
|maxWritePoolSize|Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores. Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho. O padrão é 16.|  
|messageVersion|Especifica a versão SOAP das mensagens enviadas usando a associação. Os valores válidos são<br /><br /> -Soap11Addressing10<br />-Soap12Addressing10<br /><br /> O padrão é Soap12Addressing10. Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos são<br /><br /> -UnicodeFffeTextEncoding: Unicode BigEndian codificação<br />-Utf16TextEncoding: Codificação de Unicode<br />-Utf8TextEncoding: codificação de 8 bits<br /><br /> O padrão é Utf8TextEncoding. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Codificação é o processo de transformar uma mensagem em uma sequência de bytes. Decodificação de é o processo inverso. Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e mecanismo de otimização de transmissão mensagem (MTOM).  
  
 A codificação de texto representado pelo `textMessageEncoding` elemento é o mais interoperável, mas o codificador menos eficiente para mensagens XML.  O codificador de texto cria mensagens de baseado em texto no meio físico. Produzido por esse codificador de mensagens são adequadas para WS-* com base em interoperabilidade. Serviço Web ou cliente de serviço Web geralmente pode entender XML textual. No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificação de mensagens XML.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [Escolhendo um codificador de mensagem](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Codificação de mensagens](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
