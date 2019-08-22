---
title: Elemento <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663420"
---
# <a name="thread_useallcpugroups-element"></a>\<Elemento de > Thread_UseAllCpuGroups

Especifica se o tempo de execução distribui threads gerenciados entre todos os grupos de CPU.

\<> de configuração \
\<runtime>\
\<Thread_UseAllCpuGroups>

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
|`false`|O tempo de execução não distribui threads gerenciados entre vários grupos de CPU. Esse é o padrão.|
|`true`|O tempo de execução distribui threads gerenciados entre vários grupos de CPU, se o computador tiver vários grupos de CPU e o elemento de [ \<> GCCpuGroup](gccpugroup-element.md) estiver habilitado.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

Quando um computador tem vários grupos de CPU, a habilitação desse elemento faz com que o tempo de execução distribua threads gerenciados em todos os grupos de CPU. Para usar esse recurso, você também deve habilitar o elemento de [ \<> GCCpuGroup](gccpugroup-element.md) , que estende a coleta de lixo para todos os grupos de CPU e leva todos os núcleos em conta ao criar e balancear heaps. Habilitar o [ \<elemento > GCCpuGroup](gccpugroup-element.md) requer a habilitação do [ \<elemento gcServer >](gcserver-element.md) . Se esses elementos não estiverem habilitados, a `<Thread_UseAllCpuGroups>` habilitação do elemento não terá nenhum efeito.

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

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [\<Elemento de > GCCpuGroup](gccpugroup-element.md)
