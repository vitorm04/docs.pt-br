---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a389403d58bb0b4fb4f98e25d2c9a6b2cf337281
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264617"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > elemento
Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.  
  
 \<configuration>  
\<runtime>  
\<GCCpuGroup>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Coleta de lixo não oferece suporte a vários grupos de CPU. Esse é o padrão.|  
|`true`|Coleta de lixo dá suporte a vários grupos de CPU, se a coleta de lixo do servidor estiver habilitada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Quando um computador tiver vários grupos de CPU e coleta de lixo do servidor está habilitada (consulte a [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elemento), permitindo que esse elemento se estende a coleta de lixo em todos os grupos de CPU e usa todos os núcleos em conta durante a criação e heaps de balanceamento.  
  
> [!NOTE]
>  Esse elemento só se aplica a threads de coleta de lixo. Para habilitar o tempo de execução distribui threads de usuário em todos os grupos de CPU, você deve habilitar também a [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como habilitar a coleta de lixo para vários grupos de CPU.  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Como: Desabilitar a coleta de lixo simultânea](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
- [Coleta de lixo de estação de trabalho ou de servidor](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
