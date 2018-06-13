---
title: '&lt;Thread_UseAllCpuGroups&gt; elemento'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47d8bcdb9bbb7ec6f5a5386a5ac5951ad8891c28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745585"
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; elemento
Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.  
  
 \<configuration>  
\<runtime>  
< Thread_UseAllCpuGroups >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução não distribui threads gerenciados em vários grupos de CPU. Esse é o padrão.|  
|`true`|O tempo de execução distribui threads gerenciados por vários grupos de CPU, se o computador tiver vários grupos de CPU e o [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) elemento está habilitado.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Quando um computador tiver vários grupos de CPU, a habilitação desse elemento faz com que o tempo de execução distribuir os threads gerenciados em todos os grupos de CPU. Para usar esse recurso, você também deve habilitar o [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) elemento, que estende a coleta de lixo para todos os grupos de CPU e leva em conta ao criar e balanceamento heaps a todos os núcleos. Habilitando o [ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) elemento requer a habilitação de [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento. Se esses elementos não estiverem habilitados, habilitando o `<Thread_UseAllCpuGroups>` elemento não tem nenhum efeito.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar o suporte para vários grupos de CPU.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<GCCpuGroup > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
