---
title: '&lt;mtomMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 380aa162d2bb55ac968bdd057a4bb45b2ea6abfe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452616"
---
# <a name="ltmtommessageencodinggt"></a>&lt;mtomMessageEncoding&gt;
Especifica o controle de versão de codificação e de mensagem usado para mensagens SOAP MTOM Message Transmission Optimization Mechanism () com base.  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<mtomMessageEncoding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|maxBufferSize|Um inteiro que especifica o tamanho máximo do buffer que pode ser usado.|  
|maxReadPoolSize|Um inteiro que especifica quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores. Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior. O padrão é 64.|  
|maxWritePoolSize|Um inteiro que especifica quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores. Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto de trabalho maior. O padrão é 16.|  
|messageVersion|Especifica a versão SOAP das mensagens enviadas usando a associação. Os valores válidos são<br /><br /> -Soap11Addressing1<br />-Soap12Addressing10<br /><br /> O padrão é Soap12Addressing10. Esse atributo é do tipo <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos são<br /><br /> -UnicodeFffeTextEncoding: Unicode BigEndian codificação<br />-Utf16TextEncoding: Codificação de Unicode<br />-Utf8TextEncoding: codificação de 8 bits<br /><br /> O padrão é Utf8TextEncoding. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade das mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Codificação é o processo de transformar uma mensagem em uma sequência de bytes. Decodificação de é o processo inverso. Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e MTOM Message Transmission Optimization Mechanism ().  
  
 O `MtomMessageEncoding` elemento Especifica o controle de versão de mensagem e de codificação de caractere e outras configurações usadas para mensagens usando a codificação de MTOM Message Transmission Optimization Mechanism (). MTOM é uma tecnologia eficiente para a transmissão de dados binários em mensagens do WCF. O codificador MTOM tenta criar um equilíbrio entre a eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza blocos grandes de dados binários, transmiti-los como-está, sem a conversão em seu formato codificado na base64.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [Codificação de mensagens](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Escolhendo um codificador de mensagem](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
