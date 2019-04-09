---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 32e8ed6b70a23462fac3c53d1bc353167ff67560
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113627"
---
# <a name="windowsstreamsecurity"></a>\<windowsStreamSecurity>
Especifica configurações de segurança de fluxo do Windows da associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<windowsStreamSecurity>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|protectionLevel|Define a segurança em nível de mensagem. Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos. A criptografia fornece privacidade de nível de dados durante o transporte. Os valores válidos incluem o seguinte:<br /><br /> -None: Sem proteção.<br />-Sinal: As mensagens são assinadas.<br />-   EncryptAndSign: Mensagens assinadas e criptografadas.<br /><br /> O padrão é EncryptAndSign.<br /><br /> Esse atributo é do tipo <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Transportes que usam um protocolo orientado a fluxo como TCP e pipes nomeados oferecem suporte a atualizações com base no fluxo de transporte. Especificamente, o WCF fornece atualizações de segurança. A configuração dessa segurança de transporte é encapsulada por este elemento de configuração, bem como por [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), que pode ser configurado e adicionado a uma associação personalizada  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
