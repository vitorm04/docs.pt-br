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
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153771"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedizedStringHashAlgorithm> Element
Determina se o tempo de execução do idioma comum calcula códigos hash para strings em uma base de domínio por aplicativo.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedizedStringHashAlgorithm>**  
  
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
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se os códigos hash para strings são calculados em uma base de domínio por aplicativo.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`0`|O tempo de execução do idioma comum não computa códigos hash para strings em uma base de domínio por aplicativo; um único algoritmo é usado para calcular códigos de hash de seqüência. Esse é o padrão.|  
|`1`|O tempo de execução do idioma comum calcula códigos hash para strings em uma base de domínio por aplicativo. As strings idênticas em diferentes domínios de aplicativos e em diferentes processos terão diferentes códigos de hash.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do runtime.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, <xref:System.StringComparer> a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> classe e o método usam um único algoritmo de hashing que produz um código de hash consistente entre os domínios do aplicativo. Isso equivale a `enabled` definir o `<UseRandomizedStringHashAlgorithm>` atributo do elemento para `0`. Este é o algoritmo de hash usado no .NET Framework 4.  
  
 A <xref:System.StringComparer> classe <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> e o método também podem usar um algoritmo de hash diferente que calcula códigos de hash em uma base de domínio por aplicativo. Como resultado, os códigos hash para strings equivalentes diferem entre os domínios do aplicativo. Este é um recurso de opt-in; para tirar proveito disso, você `enabled` deve `<UseRandomizedStringHashAlgorithm>` definir `1`o atributo do elemento para .  
  
 A aparência de string em uma tabela hash é tipicamente uma operação O(1). No entanto, quando um grande número de colisões ocorrem, a procuração pode se tornar uma operação O(n<sup>2).</sup> Você pode `<UseRandomizedStringHashAlgorithm>` usar o elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que por sua vez limita o número de colisões potenciais, particularmente quando as chaves das quais os códigos de hash são calculados são baseadas na entrada de dados pelos usuários.  
  
## <a name="example"></a>Exemplo  
 O exemplo a `DisplayString` seguir define uma classe que `s`inclui uma constante de string privada, cujo valor é "Isso é uma string". Também inclui um método `ShowStringHashCode` que exibe o valor de cadeia de caracteres e seu código de hash com o nome do domínio do aplicativo no qual o método está sendo executado.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Quando você executa o exemplo sem fornecer um arquivo de configuração, ele exibe uma saída semelhante à seguinte. Observe que os códigos hash para a cadeia de caracteres são idênticos nos dois domínios de aplicativo.  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Entretanto, se você adicionar o seguinte arquivo de configuração ao diretório de exemplo e, então, executar o exemplo, os códigos hash da mesma cadeia de caracteres diferirão de acordo com o domínio de aplicativo.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Quando o arquivo de configuração estiver presente, o exemplo exibe a saída a seguir:  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
