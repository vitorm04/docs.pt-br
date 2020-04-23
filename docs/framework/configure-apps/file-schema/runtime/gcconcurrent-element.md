---
title: elemento gcConcurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102899"
---
# <a name="gcconcurrent-element"></a>\<gcElemento> concomitante

Especifica se o tempo de execução do idioma comum executa a coleta de lixo em um segmento separado.

[\<>de configuração](../configuration-element.md)\
&nbsp;&nbsp;[\<>de tempo de execução](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<> gcConcurrent

## <a name="syntax"></a>Sintaxe

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`enabled`|Atributo obrigatório.<br /><br />Especifica se o runtime executa a coleta de lixo simultaneamente.|

#### <a name="enabled-attribute"></a>atributo ativado

|Valor|Descrição|
|-----------|-----------------|
|`false`|Não funciona a coleta de lixo simultaneamente.|
|`true`|Executa a coleta de lixo simultaneamente. Esse é o padrão.|

### <a name="child-elements"></a>Elementos filho

Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|

## <a name="remarks"></a>Comentários

Antes do .NET Framework 4, a coleta de lixo da estação de trabalho suportava a coleta simultânea de lixo, que realizava a coleta de lixo em segundo plano em um fio separado. No Framework 4 ,NET Framework 4, a coleta simultânea de lixo foi substituída pelo GC de fundo, que também realiza a coleta de lixo em segundo plano em um segmento separado. A partir do .NET Framework 4.5, a coleta de fundos tornou-se disponível na coleta de lixo do servidor. O elemento **gcConcurrent controla** se o tempo de execução realiza a coleta de lixo simultânea ou em segundo plano, se está disponível ou se realiza a coleta de lixo em primeiro plano.

### <a name="to-disable-background-garbage-collection"></a>Para desativar a coleta de lixo em segundo plano

> [!WARNING]
> A partir do Framework 4 .NET, a coleta simultânea de lixo é substituída pela coleta de lixo de fundo. Os termos *simultâneos* e *de fundo* são usados de forma intercambiável na documentação .NET Framework. Para desativar a coleta de lixo de fundo, utilize o elemento **gcConcurrent,** conforme discutido neste artigo.

Por padrão, o tempo de execução usa coleta de lixo simultânea ou em segundo plano, que é otimizada para latência. Se o aplicativo envolver uma forte interação do usuário, deixe a coleta de lixo simultânea habilitada a minimizar o tempo de pausa do aplicativo para realizar a coleta de lixo. Se você `enabled` definir o atributo do `false`elemento **gcConcurrent** para , o tempo de execução usará a coleta de lixo não simultânea, que é otimizada para throughput.

O arquivo de configuração a seguir desativa a coleta de lixo em segundo plano:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

Se houver uma configuração **gcConcurrentSetting** no arquivo de configuração da máquina, ele definirá o valor padrão para todos os aplicativos .NET Framework. A configuração do arquivo de configuração da máquina substitui a configuração de configuração do aplicativo.

Para obter mais informações sobre coleta de lixo simultânea e de fundo, consulte [Coleta de lixo em segundo plano](../../../../standard/garbage-collection/background-gc.md).

## <a name="example"></a>Exemplo

O exemplo a seguir permite a coleta de lixo em segundo plano:

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Confira também

- [Esquema de configurações em tempo de execução](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Noções básicas sobre a coleta de lixo](../../../../standard/garbage-collection/fundamentals.md)
