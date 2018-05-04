---
title: '&lt;EnableAmPmParseAdjustment&gt; elemento'
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17f521be31fa4082d9418c7dad734e37994bbb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltenableampmparseadjustmentgt-element"></a>&lt;EnableAmPmParseAdjustment&gt; elemento
Determina se a data e hora métodos usam um conjunto de regras de ajustada para analisar cadeias de caracteres de data que contêm um dia, mês, hora e designator AM/PM.  
  
 \<configuration>  
 \<runtime>  
\<EnableAmPmParseAdjustment >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se a data e hora métodos usarem um conjunto de regras de ajustada para analisar cadeias de caracteres de data que contêm somente um dia, mês, hora e designator AM/PM.|  
  
### <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|Data e hora métodos não usar regras ajustadas para analisar cadeias de caracteres que contêm apenas um dia, mês, hora e designator AM/PM.|  
|1|Data e hora métodos usam regras ajustadas para analisar cadeias de caracteres que contêm apenas um dia, mês, hora e designator AM/PM.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 O `<EnableAmPmParseAdjustment>` elemento controla como os métodos a seguir analisar uma cadeia de caracteres de data que contém um dia numérico e seguido por um designador de AM/PM (por exemplo, "6 de 4 a 10 AM") e uma hora do mês:  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 Não há outros padrões são afetados.  
  
 O `<EnableAmPmParseAdjustment>` elemento não tem nenhum efeito o <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, e <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> métodos.  
  
> [!IMPORTANT]
>  No .NET Core e .NET nativo, as regras de análise de AM/PM ajustadas são habilitadas por padrão.  
  
 Se a regra de ajuste a análise não estiver habilitada, o primeiro dígito da cadeia de caracteres é interpretado como a hora do relógio de 12 horas, e o restante da cadeia de caracteres, exceto o designador de AM/PM é ignorado. A data e hora retornada pelo método de análise consiste a data atual e a hora do dia extraído da cadeia de caracteres de data.  
  
 Se a regra de ajuste a análise está habilitada, análise do método interpretar o dia e mês como pertencentes ao ano atual e interpretar a hora como a hora do relógio de 12 horas.  
  
 A tabela a seguir ilustra a diferença no <xref:System.DateTime> valor quando o <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> método é usado para analisar a cadeia de caracteres "" 4/10 6 AM"com o `<EnableAmPmParseAdjustment>` do elemento `enabled` propriedade definida como"0"ou"1". Ele pressupõe que a data de hoje é 5 de janeiro de 2017 e exibe a data em que ele é formatado usando a cadeia de caracteres do formato da cultura especificada "G".  
  
|Nome da cultura|ativado = "0"|ativado = "1"|  
|------------------|------------------|------------------|  
|en-US|1/5/2017 4:00:00 AM|10/4/2017 6:00:00 AM|  
|en-GB|5/1/2017 6:00:00|10/4/2017 6:00:00|  
  
## <a name="see-also"></a>Consulte também  
 [\<tempo de execução > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
