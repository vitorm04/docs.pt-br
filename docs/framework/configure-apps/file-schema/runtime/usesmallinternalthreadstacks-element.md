---
title: Elemento <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74678089bb1b19295983064eb7ad54fbf0a1e361
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663384"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<Elemento de > UseSmallInternalThreadStacks
Solicita que o Common Language Runtime (CLR) reduza o uso de memória especificando tamanhos de pilha explícitos ao criar determinados threads que ele usa internamente, em vez de usar o tamanho de pilha padrão para esses threads.  
  
 \<Elemento de > de configuração  
\<Elemento de > de tempo de execução  
\<Elemento de > UseSmallInternalThreadStacks  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|habilitado|Atributo obrigatório.<br /><br /> Especifica se deve-se solicitar que o CLR use tamanhos de pilha explícitos em vez do tamanho de pilha padrão quando ele cria determinados threads que ele usa internamente. Os tamanhos de pilha explícitos são menores do que o tamanho de pilha padrão de 1 MB.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|true|Solicitar tamanhos de pilha explícitos.|  
|false|Use o tamanho de pilha padrão. Esse é o padrão para o .NET Framework 4.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento de configuração é usado para solicitar o uso reduzido de memória virtual em um processo, pois os tamanhos de thread explícitos usados pelo CLR para seus threads internos, se a solicitação for respeitada, serão menores do que o tamanho padrão.  
  
> [!IMPORTANT]
>  Esse elemento de configuração é uma solicitação para o CLR em vez de um requisito absoluto. No .NET Framework 4, a solicitação é respeitada apenas para a arquitetura x86. Esse elemento pode ser ignorado completamente em versões futuras do CLR, ou substituído por tamanhos de pilha explícitos que são sempre usados para threads internos selecionados.  
  
 A especificação desse elemento de configuração compensa a confiabilidade para uso menor de memória virtual se o CLR honrar a solicitação, porque tamanhos de pilha menores poderiam potencialmente causar estouros de pilha mais prováveis.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como solicitar que o CLR use tamanhos de pilha explícitos para determinados threads que ele usa internamente.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
