---
title: '&lt;UseSmallInternalThreadStacks&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c96537cad59034578d1284f7dc432e5775f3730b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;UseSmallInternalThreadStacks&gt; elemento
Solicitações que o common language runtime (CLR) reduzir memória usam com a especificação de tamanhos de pilha explícita ao criar determinados threads que ele usa internamente, em vez de usar o tamanho da pilha padrão para esses threads.  
  
 \<Configuração > elemento  
\<tempo de execução > elemento  
\<UseSmallInternalThreadStacks > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Habilitado|Atributo obrigatório.<br /><br /> Especifica se deve solicitar que os tamanhos de pilha explícita de uso CLR em vez do tamanho da pilha padrão ao criar determinados threads que ele usa internamente. Os tamanhos de pilha explícitas são menores que o tamanho da pilha padrão de 1 MB.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Tamanhos de pilha explícita de solicitações.|  
|false|Use o tamanho da pilha padrão. Esse é o padrão para o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração é usado para solicitar o uso de memória virtual reduzido em um processo, porque os tamanhos de thread explícita que o CLR usa para seus threads internos, se a solicitação for respeitada, são menores que o tamanho padrão.  
  
> [!IMPORTANT]
>  Este elemento de configuração é uma solicitação para o CLR, em vez de um requisito absoluto. No [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a solicitação é respeitada somente para x86 arquitetura. Esse elemento pode ser completamente ignorado em versões futuras do CLR ou substituído por tamanhos de pilha explícitas são sempre usados para threads internos selecionados.  
  
 Especificando a que este elemento de configuração negocia confiabilidade para menor uso de memória virtual se o CLR honra a solicitação, porque os tamanhos menores de pilha potencialmente podem tornar a pilha estoura mais provável.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como solicitar que a pilha explícita de uso do CLR para determinados tamanhos de threads que ele usa internamente.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
