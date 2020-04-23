---
title: Elemento <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102886"
---
# <a name="gccpugroup-element"></a>\<Elemento> GCCpuGroup

Especifica se a coleta de lixo oferece suporte a vários grupos de CPU.

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>do GCCpuGroup**

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
|`false`|A coleta de lixo não suporta vários grupos de CPU. Esse é o padrão.|
|`true`|A coleta de lixo suporta vários grupos de CPU, se a coleta de lixo do servidor estiver ativada.|

### <a name="child-elements"></a>Elementos filho

Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

Quando um computador tem vários grupos de CPU e [ \<](gcserver-element.md) a coleta de lixo do servidor é ativada (consulte o elemento>gcServer), a ativação desse elemento estende a coleta de lixo em todos os grupos de CPU e leva todos os núcleos em conta ao criar e equilibrar montes.

> [!NOTE]
> Este elemento se aplica apenas aos fios de coleta de lixo. Para ativar o tempo de execução para distribuir threads do usuário em todos os grupos de CPU, você também deve habilitar o [ \<elemento Thread_UseAllCpuGroups>.](thread-useallcpugroups-element.md)

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como ativar a coleta de lixo para vários grupos de CPU.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Confira também

- [Esquema de configurações em tempo de execução](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Desativar a coleta simultânea de lixo](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Coleta de lixo de estação de trabalho ou de servidor](../../../../standard/garbage-collection/workstation-server-gc.md)
