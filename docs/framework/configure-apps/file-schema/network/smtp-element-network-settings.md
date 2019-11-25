---
title: Elemento <smtp> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089095"
---
# <a name="smtp-element-network-settings"></a>\<elemento > SMTP (configurações de rede)
Configura o formato de entrega, o método de entrega e o endereço de remetente para enviar emails.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**smtp >**
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`deliveryFormat`|Especifica o formato de entrega para emails de saída. Os valores aceitáveis são SevenBit e International.|  
|`deliveryMethod`|Especifica o método de entrega para emails. Os valores aceitáveis são Network, PickupDirectoryFromIis e SpecifiedPickupDirectory.|  
|`from`|Especifica o endereço de para emails de saída.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|Configura o diretório local para um servidor SMTP (Simple Mail Transport Protocol).|  
|`network`|Configura as opções de rede para um servidor SMTP externo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[\<mailSettings> Element (Network Settings)](mailsettings-element-network-settings.md) [Elemento mailSettings> (configurações de rede)]|Configura as opções de envio de email.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir especifica os parâmetros de SMTP apropriados para enviar email usando as credenciais de rede padrão.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [Esquema de configurações de rede](index.md)
