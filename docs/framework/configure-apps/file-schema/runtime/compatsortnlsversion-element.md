---
title: Elemento <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6aef46db47f881d6a15cc1e58d46219a80194b0
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456451"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > elemento
Especifica que o tempo de execução deve usar as ordens de classificação herdadas ao executar comparações de cadeias de caracteres.  
  
 \<configuration>  
\<runtime>  
\<CompatSortNLSVersion > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica a ID de localidade cuja ordem de classificação deve ser usada.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|4096|A ID de localidade que representa uma ordem de classificação alternativa. Neste caso, 4096 representa a ordem de classificação do [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] e versões anteriores.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Pois operações de maiusculas e minúsculas, classificação e comparação de cadeia de caracteres executada pela <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> classe no .NET Framework 4 está em conformidade com o padrão Unicode 5,1, os resultados dos métodos de comparação de cadeia de caracteres, como <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> e <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> podem diferir das versões anteriores do .NET Framework. Se seu aplicativo depender de comportamento herdado, você poderá restaurar as regras de classificação e comparação de cadeia de caracteres usadas no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] e em versões anteriores ao incluir o elemento `<CompatSortNLSVersion>` no arquivo de configuração do seu aplicativo.  
  
> [!IMPORTANT]
>  Restaurar a comparação e as regras de classificação de cadeia de caracteres herdadas também requer que a biblioteca de vínculo dinâmico do arquivo sort00001000.dll esteja disponível no sistema local.  
  
 Você também pode usar regras de classificação e comparação herdadas em um domínio de aplicativo específico ao passar a cadeia de caracteres "NetFx40_Legacy20SortingBehavior" ao método <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> quando o domínio do aplicativo é criado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instância de dois objetos <xref:System.String> e chama o método <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> para compará-los ao usar as convenções da cultura atual.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Quando você executar o exemplo no .NET Framework 4, ele exibe a saída a seguir.  
  
```  
sta follows a in the sort order.  
```  
  
 Isso é completamente diferente de saída exibida quando você executa o exemplo no [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```  
sta equals a in the sort order.  
```  
  
 No entanto, se você adicionar o seguinte arquivo de configuração para o diretório de exemplo e, em seguida, executar o exemplo no .NET Framework 4, a saída é idêntica à produzida pelo exemplo quando ele é executado o [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
