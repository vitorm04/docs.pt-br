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
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089122"
---
# <a name="servicepointmanager-element-network-settings"></a>\<elemento de > servicePointManager (configurações de rede)
Configura conexões com recursos de rede.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**configurações**](settings-element-network-settings.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<servicePointManager >**

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
  
|**Attribute**|**Descrição**|  
|-------------------|---------------------|  
|`checkCertificateName`|Especifica se o sistema deve verificar se o nome no certificado corresponde ao nome de host do servidor antes de usar o certificado. O valor padrão é `true`.|  
|`checkCertificateRevocationList`|Especifica se o sistema deve verificar se o certificado foi revogado antes de usar o certificado. O valor padrão é `false`.|  
|`dnsRefreshTimeout`|Especifica por quanto tempo as resoluções de DNS (serviço de nomes de domínio) são armazenadas em cache em conjunto com a opção Round Robin do DNS, em milissegundos. O valor padrão é de 120.000 milissegundos (dois minutos).|  
|`enableDnsRoundRobin`|Especifica se as resoluções DNS de nomes de host com vários endereços IP (Internet Protocol) retornam todos os endereços ou apenas o primeiro. O valor padrão é `false`.|  
|`encryptionPolicy`|Especifica a política de criptografia aplicada a uma sessão SSL/TLS em uma instância de <xref:System.Net.ServicePointManager>. Os valores possíveis são equivalentes aos valores para a enumeração de <xref:System.Net.Security.EncryptionPolicy>. O uso de <xref:System.Security.Authentication.CipherAlgorithmType.Null> é necessário quando a política de criptografia é definida como `NoEncryption`. O valor padrão é `RequireEncryption`.|  
|`expect100Continue`|Especifica se os métodos POST devem esperar receber uma resposta `100-continue` do servidor. O valor padrão é `true`.|  
|`useNagleAlgorithm`|Especifica se as conexões controladas pelo Gerenciador de ponto de serviço usam o algoritmo Nagle. O valor padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[Configurações](settings-element-network-settings.md)|Configura as opções de rede básicaspara o namespace <xref:System.Net>.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou no arquivo de configuração do computador (Machine. config).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Esquema de configurações de rede](index.md)
