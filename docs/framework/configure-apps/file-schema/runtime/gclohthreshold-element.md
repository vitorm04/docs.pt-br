---
title: GCLOHThreshold element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451216"
---
# <a name="gclohthreshold-element"></a>GCLOHThreshold element

Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a>Sintaxe

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`enabled`|Atributo obrigatório.<br /><br />Specifies the threshold size that causes objects to go on the large object heap.|

### <a name="enabled-attribute"></a>enabled attribute

|Valor|Descrição|
|-----------|-----------------|
|`nnnn`|The threshold size, in bytes, that causes objects to go on the large object heap.|

## <a name="child-elements"></a>Elementos filho

nenhuma.

## <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

This setting was introduced in .NET Framework 4.8.

## <a name="see-also"></a>Consulte também

- [Run-time settings schema](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Noções básicas da coleta de lixo](../../../../standard/garbage-collection/fundamentals.md)
- [NET Core run-time config options for GC](../../../../core/run-time-config/garbage-collector.md)
