---
title: Elemento GCLOHThreshold
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
# <a name="gclohthreshold-element"></a>Elemento GCLOHThreshold

Especifica o tamanho do limite, em bytes, que faz com que o coletor de lixo coloque objetos na LOH (Large Object heap).

[\<configuration>](../configuration-element.md)\
> &nbsp;de [\<de tempo de execução](runtime-element.md) do &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold >

## <a name="syntax"></a>Sintaxe

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`enabled`|Atributo obrigatório.<br /><br />Especifica o tamanho do limite que faz com que os objetos vá para a heap de objeto grande.|

### <a name="enabled-attribute"></a>atributo habilitado

|Valor|Descrição|
|-----------|-----------------|
|`nnnn`|O tamanho do limite, em bytes, que faz com que os objetos vá para a heap de objeto grande.|

## <a name="child-elements"></a>Child elements

Nenhum.

## <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

Essa configuração foi introduzida no .NET Framework 4,8.

## <a name="see-also"></a>Consulte também

- [Esquema de configurações de tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Noções básicas da coleta de lixo](../../../../standard/garbage-collection/fundamentals.md)
- [Opções de configuração de tempo de execução do NET Core para GC](../../../../core/run-time-config/garbage-collector.md)
