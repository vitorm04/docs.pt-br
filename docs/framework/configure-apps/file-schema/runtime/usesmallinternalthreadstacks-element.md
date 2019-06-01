---
title: Elemento <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f098065cc005c59ec558ffa1f95202715624e7d
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456106"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<UseSmallInternalThreadStacks > elemento
Usam solicitações que o common language runtime (CLR) reduzir a memória com a especificação de tamanhos de pilha explícito ao criar certos threads que ele usa internamente, em vez de usar o tamanho da pilha padrão para esses threads.  
  
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
|habilitado|Atributo obrigatório.<br /><br /> Especifica se deve solicitar que os tamanhos de pilha explícito de uso do CLR em vez do tamanho da pilha padrão ao criar certos threads que ele usa internamente. Os tamanhos de pilha explícito são menores que o tamanho da pilha padrão de 1 MB.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Tamanhos de pilha explícito de solicitação.|  
|false|Use o tamanho da pilha padrão. Esse é o padrão para o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração é usado para solicitar o uso de memória reduzido de virtual em um processo, porque os tamanhos de thread explícitos que o CLR usa para seus threads internos, se a solicitação é atendida, são menores do que o tamanho padrão.  
  
> [!IMPORTANT]
>  Este elemento de configuração é uma solicitação para o CLR em vez de um requisito absoluto. No .NET Framework 4, a solicitação é atendida somente para x86 arquitetura. Esse elemento pode ser completamente ignorado em versões futuras do CLR ou substituído pelos tamanhos de pilha explícito que são sempre usados para threads internos selecionados.  
  
 Especificando a que este elemento de configuração negocia confiabilidade para menor uso de memória virtual se o CLR honra a solicitação, porque os tamanhos menores de pilha poderiam potencialmente tornar pilha estoura mais provável.  
  
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

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
