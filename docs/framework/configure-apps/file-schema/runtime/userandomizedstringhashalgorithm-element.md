---
title: Elemento <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a51b9fb485da605effbad0e81b8baf5e05e382a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087788"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm > elemento
Determina se o common language runtime calcula códigos hash para cadeias de caracteres em uma base de domínio do aplicativo.  
  
 \<configuration>  
\<runtime>  
\<UseRandomizedStringHashAlgorithm>  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se os códigos de hash para cadeias de caracteres são calculados em uma base de domínio do aplicativo.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`0`|O common language runtime não calcula códigos hash para cadeias de caracteres em uma base de domínio de aplicativo; um único algoritmo é usado para calcular códigos hash de cadeia de caracteres. Esse é o padrão.|  
|`1`|O common language runtime computa código hash para cadeias de caracteres em uma base de domínio do aplicativo. Cadeias de caracteres idênticas em domínios de aplicativos e processos diferentes terão códigos hash diferentes.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método usar um único algoritmo de hash que gera um código hash consistente entre domínios de aplicativo. Isso equivale a definir as `enabled` atributo do `<UseRandomizedStringHashAlgorithm>` elemento a ser `0`. Este é o algoritmo de hash usado no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 O <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método também pode usar um algoritmo de hash diferente que Compute códigos hash em uma base de domínio do aplicativo. Como resultado, os códigos de hash para cadeias de caracteres equivalentes serão diferente entre domínios de aplicativo. Esse é um recurso no consentimento; para tirar proveito dele, você deve definir a `enabled` atributo o `<UseRandomizedStringHashAlgorithm>` elemento a ser `1`.  
  
 Normalmente, a pesquisa de cadeia de caracteres em uma tabela de hash é uma operação de (1). No entanto, quando um grande número de colisões ocorre, a pesquisa pode se tornar um O (n<sup>2</sup>) operação. Você pode usar o `<UseRandomizedStringHashAlgorithm>` elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que por sua vez limita o número de conflitos em potencial, especialmente quando as chaves do qual os códigos de hash são calculados são com base na entrada de dados por usuários.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define uma `DisplayString` classe que inclui uma constante de cadeia de caracteres privados, `s`, cujo valor é "Esta é uma cadeia de caracteres." Ele também inclui um `ShowStringHashCode` método que exibe o valor de cadeia de caracteres e seu código de hash junto com o nome do domínio do aplicativo no qual o método está sendo executado.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Quando você executar o exemplo sem fornecer um arquivo de configuração, ele exibe a saída semelhante à seguinte. Observe que os códigos hash para a cadeia de caracteres são idênticos em dois domínios de aplicativo.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 No entanto, se você adicionar o seguinte arquivo de configuração para o diretório de exemplo e, em seguida, executar o exemplo, os códigos hash para a mesma cadeia de caracteres diferirão de acordo com o domínio de aplicativo.  
  
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

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
