---
title: '&lt;SMTP&gt; elemento (configurações de rede)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 56912e09d24fc83e93a91cc42b1d96dcc68210f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741887"
---
# <a name="ltsmtpgt-element-network-settings"></a>&lt;SMTP&gt; elemento (configurações de rede)
Configura o formato de entrega, o método de entrega e de endereço para enviar emails.  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`deliveryFormat`|Especifica o formato de entrega de emails de saída. Os valores aceitáveis são SevenBit e tratados internacionais.|  
|`deliveryMethod`|Especifica o método de entrega de emails. Os valores aceitáveis são specifiedPickupDirectory, pickupDirectoryFromIis e rede.|  
|`from`|Especifica o endereço para emails de saída do.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|Configura o diretório local para um servidor de transporte protocolo SMTP (Simple Mail).|  
|`network`|Configura as opções de rede para um servidor SMTP externo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[\<mailSettings> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]|Configura as opções de envio de email.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica os parâmetros apropriados de SMTP para enviar email usando as credenciais de rede padrão.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
