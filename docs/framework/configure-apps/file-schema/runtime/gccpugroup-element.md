---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430488"
---
# <a name="gccpugroup-element"></a>\<elemento de > GCCpuGroup

Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.

[ **\<configuration>** ](../configuration-element.md)\
> &nbsp;de [ **\<de tempo de execução**](runtime-element.md) do &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**

## <a name="syntax"></a>Sintaxe

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.

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

None.

### <a name="parent-elements"></a>Elementos Pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

Quando um computador tem vários grupos de CPU e a coleta de lixo do servidor está habilitada (consulte o elemento [\<gcServer >](gcserver-element.md) ), a habilitação desse elemento estende a coleta de lixo em todos os grupos de CPU e leva todos os núcleos em conta ao criar e balancear heaps.

> [!NOTE]
> Este elemento aplica-se somente a threads de coleta de lixo. Para habilitar o tempo de execução para distribuir threads de usuário em todos os grupos de CPU, você também deve habilitar o elemento [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) .

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

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Para desabilitar a coleta de lixo simultânea](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Coleta de lixo de estação de trabalho ou de servidor](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
