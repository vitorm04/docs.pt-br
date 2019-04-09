---
title: <transport> De <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a6d3dd2c24e90bdcdc6520e62dcc1dbe7ce797f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199817"
---
# <a name="transport-of-netnamedpipebinding"></a>\<transport> of \<netNamedPipeBinding>
Define as configurações de segurança de transporte para um pipe nomeado.  
  
 \<system.ServiceModel>  
\<bindings>  
\<netNamedPipeBinding>  
\<binding>  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|protectionLevel|Define o nível de proteção de pipe nomeado. Assinar mensagens minimiza o risco de um terceiro violação da mensagem enquanto estão sendo transferidos. A criptografia fornece privacidade de nível de dados durante o transporte. Os valores válidos incluem o seguinte:<br /><br /> -None: Sem proteção.<br />-Sinal: As mensagens são assinadas.<br />-   EncryptAndSign: As mensagens são criptografadas e assinadas.<br /><br /> O valor padrão é EncryptAndSign.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Define as configurações de segurança para uma associação.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
