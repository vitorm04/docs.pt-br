---
title: '&lt;TimeSpan_LegacyFormatMode&gt; elemento'
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
ms.openlocfilehash: 0faf2876680ef5ec3fc7373cae9f81eb091f47a1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753964"
---
# <a name="lttimespanlegacyformatmodegt-element"></a>&lt;TimeSpan_LegacyFormatMode&gt; elemento
Determina se o tempo de execução preserva comportamento herdado na formatação operações com <xref:System.TimeSpan?displayProperty=nameWithType> valores.  
  
 \<configuration>  
\<runtime>  
< TimeSpan_LegacyFormatMode >  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução usa comportamento formatação herdado com <xref:System.TimeSpan?displayProperty=nameWithType> valores.|  
  
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
 Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], o <xref:System.TimeSpan?displayProperty=nameWithType> estrutura implementa o <xref:System.IFormattable> interface e dá suporte a operações com cadeias de caracteres de formato padrão e personalizados de formatação. Se um método de análise encontra um especificador de formato sem suporte ou uma cadeia de caracteres de formato, ele gerará um <xref:System.FormatException>.  
  
 Em versões anteriores do .NET Framework, o <xref:System.TimeSpan> estrutura não implementou <xref:System.IFormattable> e não ofereciam suporte a cadeias de caracteres de formato. No entanto, muitos desenvolvedores por engano assumido que <xref:System.TimeSpan> ofereciam suporte a um conjunto de cadeias de caracteres de formato e usá-los em [operações de formatação composta](../../../../../docs/standard/base-types/composite-formatting.md) com métodos como <xref:System.String.Format%2A?displayProperty=nameWithType>. Em geral, se um tipo implementa <xref:System.IFormattable> e cadeias de caracteres, chamadas para métodos de formatação com formato sem suporte geralmente geram cadeias de caracteres de formato dá suporte a um <xref:System.FormatException>. No entanto, como <xref:System.TimeSpan> não implementou <xref:System.IFormattable>, o tempo de execução ignorada a cadeia de caracteres de formato e em vez disso, chamado de <xref:System.TimeSpan.ToString?displayProperty=nameWithType> método. Isso significa que, embora as cadeias de caracteres de formato não tinham nenhum efeito sobre a operação de formatação, sua presença não resultou em um <xref:System.FormatException>.  
  
 Para casos em que código herdado passa uma composição formatação de método e uma cadeia de caracteres de formato inválido e que o código não pode ser recompilado, você pode usar o `<TimeSpan_LegacyFormatMode>` elemento restaurar herdado <xref:System.TimeSpan> comportamento. Quando você define o `enabled` atributos desse elemento `true`, composição formatação método resulta em uma chamada para <xref:System.TimeSpan.ToString?displayProperty=nameWithType> em vez de <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>e um <xref:System.FormatException> não é gerada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.TimeSpan> objeto e tentar formatá-lo com o <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> método usando uma cadeia de caracteres de formato padrão sem suporte.  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 Quando você executar o exemplo no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] ou uma versão anterior, ele exibe a saída a seguir:  
  
```  
12:30:45  
```  
  
 Isso difere significativamente da saída se você executar o exemplo no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou versão posterior:  
  
```  
Invalid Format  
```  
  
 No entanto, se você adicionar o arquivo de configuração a seguir ao exemplo do diretório e, em seguida, executar o exemplo [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ou versão posterior, a saída é idêntica ao produzido pelo exemplo de quando ele é executado em [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
