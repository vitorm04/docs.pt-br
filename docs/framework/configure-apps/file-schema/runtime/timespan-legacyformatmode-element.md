---
title: Elemento <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: c835e1bcef7bbfdc990c8db177eafed4ec6bb30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115208"
---
# <a name="timespan_legacyformatmode-element"></a>\<elemento de > TimeSpan_LegacyFormatMode

Determina se o tempo de execução preserva o comportamento herdado nas operações de formatação com <xref:System.TimeSpan?displayProperty=nameWithType> valores.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<TimeSpan_LegacyFormatMode >**  

## <a name="syntax"></a>Sintaxe

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução usa comportamento de formatação herdado com <xref:System.TimeSpan?displayProperty=nameWithType> valores.|

## <a name="enabled-attribute"></a>Atributo habilitado

|Valor|Descrição|
|-----------|-----------------|
|`false`|O tempo de execução não restaura o comportamento de formatação herdado.|
|`true`|O tempo de execução restaura o comportamento de formatação herdado.|

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|

## <a name="remarks"></a>Comentários

Começando com o .NET Framework 4, a estrutura de <xref:System.TimeSpan?displayProperty=nameWithType> implementa a interface <xref:System.IFormattable> e dá suporte a operações de formatação com cadeias de caracteres de formato padrão e personalizadas. Se um método de análise encontrar um especificador de formato sem suporte ou uma cadeia de caracteres de formato, ele lançará um <xref:System.FormatException>.

Nas versões anteriores do .NET Framework, a estrutura de <xref:System.TimeSpan> não implementou <xref:System.IFormattable> e não oferecia suporte a cadeias de caracteres de formato. No entanto, muitos desenvolvedores assumiram erroneamente que <xref:System.TimeSpan> davam suporte a um conjunto de cadeias de caracteres de formato e os usaram em [operações de formatação composta](../../../../standard/base-types/composite-formatting.md) com métodos como <xref:System.String.Format%2A?displayProperty=nameWithType>. Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres de formato, as chamadas para métodos de formatação com cadeias de caracteres de formato sem suporte geralmente geram um <xref:System.FormatException>. No entanto, como <xref:System.TimeSpan> não implementou <xref:System.IFormattable>, o tempo de execução ignorou a cadeia de caracteres de formato e, em vez disso, chamou o método <xref:System.TimeSpan.ToString?displayProperty=nameWithType>. Isso significa que, embora as cadeias de caracteres de formato não tenham efeito sobre a operação de formatação, sua presença não resultou em um <xref:System.FormatException>.

Para casos em que o código herdado passa um método de formatação composto e uma cadeia de caracteres de formato inválida, e esse código não pode ser recompilado, você pode usar o elemento `<TimeSpan_LegacyFormatMode>` para restaurar o comportamento de <xref:System.TimeSpan> herdado. Quando você define o atributo `enabled` desse elemento como `true`, o método de formatação composta resulta em uma chamada para <xref:System.TimeSpan.ToString?displayProperty=nameWithType> em vez de <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>e uma <xref:System.FormatException> não é gerada.

## <a name="example"></a>Exemplo

O exemplo a seguir instancia um objeto <xref:System.TimeSpan> e tenta formatá-lo com o método <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> usando uma cadeia de caracteres de formato padrão sem suporte.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Quando você executa o exemplo no .NET Framework 3,5 ou em uma versão anterior, ele exibe a seguinte saída:

```
12:30:45
```

Isso difere de acordo com a saída se você executar o exemplo na versão .NET Framework 4 ou posterior:

```
Invalid Format
```

No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo na versão .NET Framework 4 ou posterior, a saída será idêntica à produzida pelo exemplo quando for executada em .NET Framework 3,5.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
