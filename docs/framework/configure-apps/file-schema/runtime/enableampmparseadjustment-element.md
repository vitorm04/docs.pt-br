---
title: '&lt;EnableAmPmParseAdjustment&gt; Element'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97bb5912ec4d384260e3809166efacded8e2b389
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679091"
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt; Element
Determina se a data e hora de métodos de análise usam um conjunto de regras ajustado para analisar cadeias de caracteres de data que contêm um dia, mês, hora e designador AM/PM.  
  
 \<configuration>  
 \<runtime>  
\<EnableAmPmParseAdjustment>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se a data e hora de métodos de análise usam um conjunto de regras ajustado para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designador AM/PM.|  
  
### <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Data e hora de métodos de análise não usam regras ajustadas para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designador AM/PM.|  
|1|Data e hora métodos de análise usam regras ajustadas para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designador AM/PM.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 O `<EnableAmPmParseAdjustment>` elemento controla como os métodos a seguir analisar uma cadeia de caracteres de data que contém um dia numérico e o mês, seguido por uma hora e um designador AM/PM (por exemplo, "10 4 6 AM"):  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Outros padrões não são afetados.  
  
 O `<EnableAmPmParseAdjustment>` elemento não tem efeito sobre a <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, e <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> métodos.  
  
> [!IMPORTANT]
>  No .NET Core e .NET Native, regras de análise ajustadas do AM/PM são habilitadas por padrão.  
  
 Se a regra de análise de ajuste não estiver habilitada, o primeiro dígito da cadeia de caracteres é interpretado como a hora do relógio de 12 horas, e o restante da cadeia de caracteres, exceto o designador AM/PM é ignorado. A data e hora retornado pelo método de análise consiste da data atual e a hora do dia extraído da cadeia de caracteres de data.  
  
 Se a regra de análise de ajuste está habilitada, método de análise interpretar o dia e mês como pertencentes ao ano atual e interpretar a hora como a hora do relógio de 12 horas.  
  
 A tabela a seguir ilustra a diferença no <xref:System.DateTime> valor quando o <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> método é usado para analisar a cadeia de caracteres "" 4/10 6 AM"com o `<EnableAmPmParseAdjustment>` do elemento `enabled` propriedade definida como"0"ou"1". Ele pressupõe que hoje é dia 5 de janeiro de 2017 e exibe a data como se ele é formatado usando a cadeia de caracteres de formato de "G" da cultura especificada.  
  
|Nome da cultura|enabled="0"|enabled="1"|  
|------------------|------------------|------------------|  
|en-US|1/5/2017 4:00:00 AM|4/10/2017 6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Consulte também
- [\<tempo de execução > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
