---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56b23b6d5fca6d0527d509c9b6a6fc6dd82336
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920777"
---
# <a name="gccpugroup-element"></a>\<Elemento de > GCCpuGroup

Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.

\<> de configuração \
\<runtime>\
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
|`false`|A coleta de lixo não dá suporte a vários grupos de CPU. Esse é o padrão.|
|`true`|A coleta de lixo oferece suporte a vários grupos de CPU, se a coleta de lixo do servidor estiver habilitada.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

Quando um computador tem vários grupos de CPU e a coleta de lixo do servidor está habilitada (consulte o elemento [ \<gcServer >](gcserver-element.md) ), a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU e leva todos os núcleos em conta ao criar e balanceamento de heaps.

> [!NOTE]
> Este elemento aplica-se somente a threads de coleta de lixo. Para habilitar o tempo de execução para distribuir threads de usuário em todos os grupos de CPU, você também deve habilitar o elemento de [ \<> Thread_UseAllCpuGroups](thread-useallcpugroups-element.md) .

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

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Para desabilitar a coleta de lixo simultânea](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Coleta de lixo de estação de trabalho ou de servidor](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
