---
title: Elemento <servicePointManager> (Configurações de Rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: 407ed85de109a671030eccff8ddd92af91628014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202203"
---
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager > (configurações de rede)
Configura as conexões aos recursos da rede.  
  
 \<configuration>  
\<system.net>  
\<Configurações >  
\<servicePointManager>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`checkCertificateName`|Especifica se o sistema deve verificar o nome do certificado coincide com o nome de host do servidor antes de usar o certificado. O valor padrão é `true`.|  
|`checkCertificateRevocationList`|Especifica se o sistema deve verificar se o certificado foi revogado antes de usar o certificado. O valor padrão é `false`.|  
|`dnsRefreshTimeout`|Especifica quanto tempo domínio nome DNS (serviço) resoluções são armazenados em cache em conjunto com a opção de Round Robin de DNS, em milissegundos. O valor padrão é de 120.000 milissegundos (dois minutos).|  
|`enableDnsRoundRobin`|Especifica se as resoluções DNS do host de nomes com retorno de vários endereços IP (Internet Protocol), todos os endereços, ou apenas a primeira. O valor padrão é `false`.|  
|`encryptionPolicy`|Especifica a política de criptografia aplicada a uma sessão SSL/TLS em um <xref:System.Net.ServicePointManager> instância. Os valores possíveis são equivalentes aos valores para o <xref:System.Net.Security.EncryptionPolicy> enumeração. O uso de <xref:System.Security.Authentication.CipherAlgorithmType.Null> é necessária quando a política de criptografia é definida como `NoEncryption`. O valor padrão é `RequireEncryption`.|  
|`expect100Continue`|Especifica se os métodos POST devem esperar receber um `100-continue` resposta do servidor. O valor padrão é `true`.|  
|`useNagleAlgorithm`|Especifica se as conexões controladas pelo Gerenciador de ponto de serviço usar o algoritmo de Nagle. O valor padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Configurações](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
