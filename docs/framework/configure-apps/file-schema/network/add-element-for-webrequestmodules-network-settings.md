---
title: "&lt;Adicionar&gt; elemento webRequestModules (configurações de rede)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd407f77e75bce4bdbc37acd5f28bbe39f92d564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a>&lt;Adicionar&gt; elemento webRequestModules (configurações de rede)
Adiciona um módulo de solicitação da Web personalizado para o aplicativo.  
  
 \<configuration>  
\<System.NET >  
\<webRequestModules >  
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
|`prefix`|O prefixo do URI para solicitações tratadas por este módulo de solicitação da Web.|  
|`type`|O nome de tipo totalmente qualificado (indicado pelo <xref:System.Type.FullName%2A> propriedade) e o nome do assembly (indicado pelo <xref:System.Reflection.Assembly.FullName%2A> propriedade), separados por uma vírgula, que implementa este módulo de solicitação da Web.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|**Elemento**|**Descrição**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Especifica módulos a ser usado para solicitar informações de hosts de rede.|  
  
## <a name="remarks"></a>Comentários  
 O `prefix` atributo define o prefixo URI que usa o módulo de solicitação da Web especificado. Módulos de solicitação da Web geralmente são registrados para lidar com um protocolo específico, como HTTP ou FTP, mas podem ser registrados para manipular uma solicitação para um servidor específico ou em um servidor.  
  
 O módulo de solicitação da Web é criado quando um correspondência de prefixo do URI é passado para o <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> método.  
  
 O valor para o `prefix` atributo deve ser os caracteres à esquerda de um URI válido – por exemplo, "http" ou "http://www.contoso.com".  
  
 O valor para o `type` atributo deve ser um nome de tipo válido e o nome de assembly correspondente, separados por uma vírgula.  
  
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
 <xref:System.Net.WebRequest>  
 [Esquema de configurações de rede](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
