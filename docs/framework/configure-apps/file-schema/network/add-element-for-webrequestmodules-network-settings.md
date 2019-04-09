---
title: <add> Elemento para webRequestModules (configurações de rede)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 4c1116c088c12ad3859714c8d75704d0156c12f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188223"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<Adicionar > elemento para webRequestModules (configurações de rede)
Adiciona um módulo de solicitação da Web personalizado para o aplicativo.  
  
 \<configuration>  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|**Atributo**|**Descrição**|  
|-------------------|---------------------|  
|`prefix`|O prefixo URI para solicitações manipuladas por esse módulo de solicitação da Web.|  
|`type`|O nome do tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula, que implementa este módulo de solicitação da Web.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Especifica os módulos para usá-lo para solicitar informações de hosts da rede.|  
  
## <a name="remarks"></a>Comentários  
 O `prefix` atributo define o prefixo URI que usa o módulo de solicitação da Web especificado. Módulos de solicitação da Web geralmente são registrados para lidar com um protocolo específico, como HTTP ou FTP, mas podem ser registrados para manipular uma solicitação para um servidor específico ou um caminho em um servidor.  
  
 O módulo de solicitação da Web é criado quando um prefixo URI correspondente é passado para o <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> método.  
  
 O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido. Por exemplo `http` ou `http://www.contoso.com`.
  
 O valor para o `type` atributo deve ser um nome de tipo válido e o nome do assembly correspondente, separados por vírgula.
  
## <a name="configuration-files"></a>Arquivos de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do aplicativo ou o arquivo de configuração de máquina (Machine. config).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir registra um módulo de solicitação da Web personalizado para HTTP. Você deve substituir os valores de versão e PublicKeyToken com os valores corretos para o módulo especificado.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.WebRequest>
- [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
