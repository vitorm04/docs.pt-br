---
title: '&lt;UseRandomizedStringHashAlgorithm&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7cd561cf0e0a9e080b150bdaa412686126423c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;UseRandomizedStringHashAlgorithm&gt; elemento
Determina se o common language runtime calcula os códigos de hash para cadeias de caracteres em um por cada domínio de aplicativo.  
  
 \<configuration>  
\<tempo de execução >  
\<UseRandomizedStringHashAlgorithm >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se os códigos de hash para cadeias de caracteres são calculados em um por cada domínio de aplicativo.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`0`|O common language runtime não computa códigos hash para cadeias de caracteres em um por cada domínio de aplicativo; um único algoritmo é usado para calcular os códigos de hash da cadeia de caracteres. Esse é o padrão.|  
|`1`|O common language runtime calcula os códigos de hash para cadeias de caracteres em um por cada domínio de aplicativo. Cadeias de caracteres idênticas em diferentes domínios de aplicativo em diferentes processos terão códigos hash diferente.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método usa um único algoritmo de hash que gera um código hash consistente entre domínios de aplicativo. Isso é equivalente à configuração de `enabled` atributo do `<UseRandomizedStringHashAlgorithm>` elemento `0`. Este é o algoritmo de hash usado no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 O <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método também pode usar outro algoritmo de hash que calcula códigos hash em um por cada domínio de aplicativo. Como resultado, os códigos de hash para cadeias de caracteres equivalentes variam entre domínios de aplicativo. Esse é um recurso de aceitação; para tirar proveito dele, você deve definir o `enabled` atributo do `<UseRandomizedStringHashAlgorithm>` elemento `1`.  
  
 A pesquisa de cadeia de caracteres em uma tabela de hash é normalmente uma operação de (1). No entanto, quando um grande número de conflitos ocorrerem, a pesquisa pode se tornar um O (n<sup>2</sup>) operação. Você pode usar o `<UseRandomizedStringHashAlgorithm>` elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que por sua vez limita o número de conflitos potenciais, especialmente quando as chaves do qual os códigos de hash são calculados se baseiam em dados de entrada por usuários.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `DisplayString` classe que inclui uma constante de cadeia de caracteres privada, `s`, cujo valor é "É uma cadeia de caracteres." Ele também inclui um `ShowStringHashCode` método que exibe o valor de cadeia de caracteres e o código de hash junto com o nome do domínio do aplicativo no qual o método está em execução.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Quando você executa o exemplo sem fornecer um arquivo de configuração, ele exibe a saída semelhante à seguinte. Observe que os códigos de hash para a cadeia de caracteres são idênticos nos domínios de aplicativo de dois.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 No entanto, se você adicionar o seguinte arquivo de configuração para o diretório de exemplo e, em seguida, executa o exemplo, os códigos de hash para a mesma cadeia de caracteres serão diferentes por domínio de aplicativo.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Quando o arquivo de configuração estiver presente, o exemplo exibe a saída a seguir:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
