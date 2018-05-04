---
title: '&lt;developmentMode&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b4eb1dfb50774cea2f7a50d5e5350b0338f41e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdevelopmentmodegt-element"></a>&lt;developmentMode&gt; elemento
Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.  
  
 \<configuration>  
\<runtime>  
\<developmentMode >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**developerInstallation**|Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|**true**|Procura assemblies nos diretórios especificados pela variável de ambiente DEVPATH.|  
|**false**|Não procurar por assemblies nos diretórios especificados pela variável de ambiente DEVPATH. Esse é o padrão|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Use essa configuração somente em tempo de desenvolvimento. O tempo de execução não verifica as versões em assemblies de nomes fortes encontrados no DEVPATH. Ele simplesmente usa o primeiro conjunto que encontrar.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como fazer com que o tempo de execução procurar por assemblies nos diretórios especificados pela variável de ambiente DEVPATH.  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Como localizar assemblies usando DEVPATH](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
