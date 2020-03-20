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
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154264"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion> Element
Especifica que o runtime deve usar as ordens de classificação herdadas ao executar comparações de cadeias de caracteres.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
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
|4096|A ID de localidade que representa uma ordem de classificação alternativa. Neste caso, 4096 representa a ordem de classificação do .NET Framework 3.5 e versões anteriores.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
  
## <a name="remarks"></a>Comentários  
 Como as operações de comparação, classificação <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> e invólucro de seqüência de caracteres realizadas pela classe <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> no <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> Quadro .NET 4 estão em conformidade com a norma Unicode 5.1, os resultados de métodos de comparação de strings, como e podem diferir das versões anteriores do Quadro .NET. Se o aplicativo depender do comportamento legado, você pode restaurar as regras de comparação e classificação `<CompatSortNLSVersion>` de strings usadas no .NET Framework 3.5 e versões anteriores, incluindo o elemento no arquivo de configuração do aplicativo.  
  
> [!IMPORTANT]
> Restaurar a comparação e as regras de classificação de cadeia de caracteres herdadas também requer que a biblioteca de vínculo dinâmico do arquivo sort00001000.dll esteja disponível no sistema local.  
  
 Você também pode usar regras de classificação e comparação herdadas em um domínio de aplicativo específico ao passar a cadeia de caracteres "NetFx40_Legacy20SortingBehavior" ao método <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> quando o domínio do aplicativo é criado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma instância de dois objetos <xref:System.String> e chama o método <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> para compará-los ao usar as convenções da cultura atual.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Quando você executa o exemplo no .NET Framework 4, ele exibe a seguinte saída:
  
```console
sta follows a in the sort order.  
```  
  
 Isso é completamente diferente da saída exibida quando você executa o exemplo no .NET Framework 3.5:
  
```console
sta equals a in the sort order.  
```  
  
 No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo no .NET Framework 4, a saída é idêntica à produzida pelo exemplo quando é executada no .NET Framework 3.5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
