---
title: '&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c2dfd5d3944618cf94d32fac2708d6daef5a410
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613681"
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; elemento
Especifica se o tempo de execução usa uma quantidade fixa de memória para calcular códigos hash para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.  
  
 \<configuration>  
\<runtime>  
< NetFx45_CultureAwareComparerGetHashCode_LongStrings >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o Common Language Runtime atribui uma quantidade fixa de memória ao calcular códigos hash.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|0|O Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash. Esse é o padrão.|  
|1|O Common Language Runtime aloca uma quantidade fixa de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> para calcular códigos hash.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o Common Language Runtime aloca uma quantidade variável de memória para o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> e um <xref:System.ArgumentException> pode ser disparado quando o método tentar calcular o código hash de cadeias de caracteres muito grandes (com comprimentos superiores a vários milhões de caracteres). Ao adicionar esse elemento a um arquivo de configuração do aplicativo e definir seu atributo `enabled` como "1", você poderá especificar que o método <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> use um algoritmo alternativo que aloque uma quantidade fixa de memória para o cálculo de códigos hash.  
  
> [!IMPORTANT]
>  O elemento `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` não é usado em [!INCLUDE[win8](../../../../../includes/win8-md.md)] e versões posteriores.  
  
## <a name="see-also"></a>Consulte também  
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
