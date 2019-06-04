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
ms.openlocfilehash: 31e2a075f9202439cd62c81a06528b20c4971656
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489341"
---
# <a name="timespanlegacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode > elemento
Determina se o tempo de execução preserva o comportamento herdado na formatação de operações com <xref:System.TimeSpan?displayProperty=nameWithType> valores.  
  
 \<configuration>  
\<runtime>  
<TimeSpan_LegacyFormatMode>  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução usa o comportamento herdado de formatação com <xref:System.TimeSpan?displayProperty=nameWithType> valores.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|O tempo de execução não restaura o comportamento herdado de formatação.|  
|`true`|O tempo de execução restaura o comportamento herdado de formatação.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Começando com o .NET Framework 4, o <xref:System.TimeSpan?displayProperty=nameWithType> estrutura implementa o <xref:System.IFormattable> interface e dá suporte a operações com cadeias de caracteres de formato padrão e personalizados de formatação. Se um método de análise encontra um especificador de formato sem suporte ou uma cadeia de caracteres de formato, ele gerará um <xref:System.FormatException>.  
  
 Nas versões anteriores do .NET Framework, o <xref:System.TimeSpan> estrutura não implementou <xref:System.IFormattable> e não ofereciam suporte a cadeias de caracteres de formato. No entanto, muitos desenvolvedores, por engano, supõe-se que <xref:System.TimeSpan> oferecia suporte a um conjunto de cadeias de caracteres de formato e usá-los na [operações de formatação de composição](../../../../../docs/standard/base-types/composite-formatting.md) com métodos como <xref:System.String.Format%2A?displayProperty=nameWithType>. Normalmente, se um tipo implementa <xref:System.IFormattable> e dá suporte a cadeias de caracteres, chamadas para métodos de formatação com formato sem suporte geralmente geram cadeias de caracteres de formato um <xref:System.FormatException>. No entanto, porque <xref:System.TimeSpan> não implementa <xref:System.IFormattable>, o tempo de execução ignorada a cadeia de caracteres de formato e chamado em vez disso, o <xref:System.TimeSpan.ToString?displayProperty=nameWithType> método. Isso significa que, embora as cadeias de caracteres de formato não tinham efeito sobre a operação de formatação, sua presença não resultou em um <xref:System.FormatException>.  
  
 Para casos em que código herdado passa uma método e uma cadeia de caracteres de formato inválido de formatação de composição e que o código não pode ser recompilado, você pode usar o `<TimeSpan_LegacyFormatMode>` elemento para restaurar herdado <xref:System.TimeSpan> comportamento. Quando você define o `enabled` atributo desse elemento para `true`, o método resulta em uma chamada para formatação de composição <xref:System.TimeSpan.ToString?displayProperty=nameWithType> vez <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>e um <xref:System.FormatException> não é lançada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir instancia um <xref:System.TimeSpan> objeto e tentar formatá-la com o <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> método usando uma cadeia de caracteres de formato padrão sem suporte.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Quando você executa o exemplo no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ou em uma versão anterior, ele exibe a seguinte saída:  
  
```  
12:30:45  
```  
  
 Isso difere significativamente da saída se você executar o exemplo no .NET Framework 4 ou versão posterior:  
  
```  
Invalid Format  
```  
  
 No entanto, se você adicionar o seguinte arquivo de configuração para o diretório de exemplo e, em seguida, executar o exemplo no .NET Framework 4 ou versão posterior, a saída será idêntica à produzida pelo exemplo quando ele é executado em [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
