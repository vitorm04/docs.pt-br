---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: fc1f83128dacb588d8179dea95c132da1ab2be91
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755260"
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Habilita XML de texto simples, codificações mensagem JSON (JavaScript Object Notation) e conteúdo binário "bruto" para ser lido e gravado quando usado em uma associação WCF (Windows Communication Foundation).  
  
 \<system.serviceModel>  
\<associações >  
\<customBinding>  
\<associação >  
\<webMessageEncoding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`maxReadPoolSize`|A quantidade de mensagens que podem ser lidas simultaneamente sem alocar novos leitores. Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho. O padrão é 64 leitores para cada um dos codificadores internos (texto JSON e "brutos").<br /><br /> Aumentar esse número consumo de memória aumenta, mas prepara o codificador para lidar com picos repentinos de mensagens de entrada porque ele é capaz de usar os leitores do pool que já foram criados em vez de criar novos.|  
|`maxWritePoolSize`|A quantidade de mensagens que podem ser enviadas simultaneamente sem alocar novos escritores. Tamanhos maiores de pool tornam o sistema mais tolerantes a picos de atividade às custas de um conjunto maior de trabalho. O padrão é 16 gravadores para cada um dos codificadores internos (texto JSON e "brutos").<br /><br /> Aumentar esse número consumo de memória aumenta, mas prepara o codificador para lidar com picos repentinos de mensagens de saída porque ele é capaz de usar gravadores do pool que já foram criados em vez de criar novos.|  
|`writeEncoding`|Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos são:<br /><br /> -UnicodeFffeTextEncoding: Big Endian codificação Unicode.<br />-Utf16TextEncoding: A codificação Unicode.<br />-Utf8TextEncoding: codificação de 8 bits.<br /><br /> O padrão é Utf8TextEncoding. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Codificação é o processo de transformar uma mensagem em uma sequência de bytes. Decodificação de é o processo inverso. Esses processos exigem a especificação de uma codificação de caracteres.  
  
 O `webMessageEncoding` elemento funciona delegando a uma série de codificadores internas para lidar com codificações XML e JSON em texto sem formatação e dados binários "brutos". Essa delegação é feita por um codificador de mensagem composto.  
  
 Esse elemento de associação e seu codificador composto são usados para controlar a codificação em cenários que não usam mensagens SOAP usada pelo `webHttpBinding` elemento. Esses cenários incluem "Plain Old XML" (POX), REST Representational State Transfer (), RSS Really Simple Syndication () e Atom distribuição e JavaScript assíncrono e XML (AJAX). O codificador de mensagem composto não oferece suporte a SOAP ou WS-Addressing.  
  
 O elemento de associação pode ser configurado com uma codificação de caracteres de gravação usando o `writeEncoding` atributo. Fornecido <xref:System.Text.Encoding> valor Especifica o comportamento de gravação para os casos JSON e XML Textual. Leitura, qualquer codificação de mensagem válido e a codificação de texto é entendido.  
  
 `maxReadPoolSize` e `maxWritePoolSize` também pode ser usado para definir o número máximo de leitores e gravadores a ser alocada respectivamente. Por padrão, são alocados 64 leitores e 16 gravadores.  
  
 Restrições de complexidade padrão também são definidas usando o [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) elemento para proteger contra uma classe de negação de serviço (DOS) ataques que tentem usar complexidade de mensagem para ligar o processamento do ponto de extremidade recursos.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Codificação de mensagens](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Escolhendo um codificador de mensagem](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
