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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bd74460c7d5d077686c723936d140b07ac21dd0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663400"
---
# <a name="timespan_legacyformatmode-element"></a>\<Elemento de > TimeSpan_LegacyFormatMode

Determina se o tempo de execução preserva o comportamento herdado nas operações <xref:System.TimeSpan?displayProperty=nameWithType> de formatação com valores.

\<> de configuração \
\<runtime>\
\<TimeSpan_LegacyFormatMode>

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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução usa comportamento de <xref:System.TimeSpan?displayProperty=nameWithType> formatação herdado com valores.|

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

Começando com o .NET Framework 4, a <xref:System.TimeSpan?displayProperty=nameWithType> estrutura implementa a <xref:System.IFormattable> interface e dá suporte a operações de formatação com cadeias de caracteres de formato padrão e personalizadas. Se um método de análise encontrar um especificador de formato sem suporte ou uma cadeia de caracteres de <xref:System.FormatException>formato, ele lançará um.

Nas versões anteriores do .NET Framework, a estrutura <xref:System.TimeSpan> não implementou <xref:System.IFormattable> e não oferecia suporte a cadeias de caracteres de formato. No entanto, muitos desenvolvedores assumiram erroneamente <xref:System.TimeSpan> que davam suporte a um conjunto de cadeias de caracteres de formato e os usaram em <xref:System.String.Format%2A?displayProperty=nameWithType> [operações de formatação composta](../../../../../docs/standard/base-types/composite-formatting.md) com métodos como. Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres de formato, as chamadas para métodos de formatação com <xref:System.FormatException>cadeias de caracteres de formato sem suporte geralmente lançam um. No entanto <xref:System.TimeSpan> , como o <xref:System.IFormattable>não foi implementado, o Runtime ignorou a cadeia de <xref:System.TimeSpan.ToString?displayProperty=nameWithType> caracteres de formato e, em vez disso, chamou o método. Isso significa que, embora as cadeias de caracteres de formato não tenham efeito sobre a operação de formatação, sua presença <xref:System.FormatException>não resultou em um.

Para casos em que o código herdado passa um método de formatação composto e uma cadeia de caracteres de formato inválida, e esse código não pode ser `<TimeSpan_LegacyFormatMode>` recompilado, você pode <xref:System.TimeSpan> usar o elemento para restaurar o comportamento herdado. Quando você define o `enabled` atributo desse elemento como `true`, o método de formatação composta resulta em uma chamada para <xref:System.TimeSpan.ToString?displayProperty=nameWithType> em vez <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>de e um <xref:System.FormatException> não é gerado.

## <a name="example"></a>Exemplo

O exemplo a seguir instancia um <xref:System.TimeSpan> objeto e tenta formatá-lo com <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> o método usando uma cadeia de caracteres de formato padrão sem suporte.

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
