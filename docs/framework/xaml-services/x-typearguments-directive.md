---
title: Diretiva x:TypeArguments
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 1d1b10b4da1263843bdce5447f0716569c7700e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085799"
---
# <a name="xtypearguments-directive"></a>Diretiva x:TypeArguments
Passa a restrição de tipo de argumentos de um genérico para o construtor do tipo genérico.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`object`|Uma declaração de elemento de objeto de um tipo XAML, que é apoiada por um tipo genérico do CLR. Se `object` refere-se a um tipo XAML que não é do namespace XAML padrão, `object` requer um prefixo para indicar o namespace XAML em que `object` existe.|  
|`typeString`|Uma cadeia de caracteres que declara um ou mais XAML Digite nomes como cadeias de caracteres, que fornece os argumentos de tipo para o tipo genérico do CLR. Consulte os comentários para observações sobre a sintaxe adicional.|  
  
## <a name="remarks"></a>Comentários  
 Na maioria dos casos, os tipos XAML que são usados como um item de informações em um `typeString` cadeia de caracteres têm o prefixo. Tipos típicos de restrições genéricas do CLR (por exemplo, <xref:System.Int32> e <xref:System.String>) provenientes de bibliotecas de classes base do CLR. Essas bibliotecas não são mapeadas para típico padrão de específicas da estrutura XAML namespaces e, portanto, exigem um prefixo de mapeamento para o uso do XAML.  
  
 Você pode especificar mais de um nome de tipo XAML usando um delimitador de vírgula.  
  
 Se as restrições genéricas em si usam tipos genéricos, os argumentos de tipo de restrição aninhadas podem estar contidos por parênteses ().  
  
 Observe que essa definição de `x:TypeArguments` é específico para serviços de XAML do .NET Framework e usando o CLR de retorno. Uma definição de nível de linguagem pode ser encontrada em [ \[MS-XAML\] seção 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Exemplos de uso  
 Nestes exemplos, suponha que as seguintes definições de namespace XAML são declaradas:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Lista\<cadeia de caracteres >  
 `<scg:List x:TypeArguments="sys:String" ...>` cria uma nova <xref:System.Collections.Generic.List%601> com um <xref:System.String> argumento de tipo.  
  
### <a name="dictionarystringstring"></a>Dicionário\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` cria uma nova <xref:System.Collections.Generic.Dictionary%602> com dois <xref:System.String> argumentos de tipo.  
  
### <a name="queuekeyvaluepairstringstring"></a>Fila < KeyValuePair\<String, String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` cria uma nova <xref:System.Collections.Generic.Queue%601> que tem uma restrição de <xref:System.Collections.Generic.KeyValuePair%602> com os argumentos de tipo de restrição interna <xref:System.String> e <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Usos XAML genérico do XAML 2006 e o WPF  
 Para uso do XAML 2006 e XAML que é usado para aplicativos do WPF, existem as seguintes restrições para `x:TypeArguments` e usos de tipo genérico do XAML em geral:  
  
-   Apenas o elemento raiz de um arquivo XAML pode dar suporte a um uso genérico de XAML que faz referência a um tipo genérico.  
  
-   O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>. As funções de página são o cenário principal para suporte ao uso de genéricos de XAML no WPF.  
  
-   O elemento de objeto XAML de elemento raiz para o genérico também deve declarar uma classe parcial usando `x:Class`. Isso é verdadeiro mesmo se a ação de build definindo um WPF.  
  
-   `x:TypeArguments` não é possível fazer referência a restrições genéricas aninhadas.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou XAML 2006 sem 3.0 do WPF ou WPF 3.5 dependência  
 Em serviços de XAML .NET Framework para XAML 2006 ou XAML 2009, as restrições relacionadas a WPF no uso de genéricos XAML são reduzidas. Você pode instanciar um elemento de objeto genérico em qualquer posição na marcação XAML que o modelo de objeto e de sistema de tipo backup pode dar suporte.  
  
 Se você usar o XAML 2009 em vez de mapeamento do CLR tipos para obter tipos XAML para primitivos de linguagem comuns de base, você pode usar [tipos inseridos para primitivos de linguagem XAML comuns](built-in-types-for-common-xaml-language-primitives.md) como itens de informações em um `typeString`. Por exemplo, você poderia declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o namespace XAML de linguagem XAML para o XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 No WPF e ao direcionar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar recursos do XAML 2009 junto com `x:TypeArguments` , mas somente para XAML flexível (XAML não é compilado por marcação). Compilado por marcação XAML para WPF e o formato BAML de XAML têm suporte no momento, as palavras-chave do XAML 2009 e os recursos. Se você precisa para marcação de compilar o XAML, você deve operar sob as restrições na seção "XAML 2006 and genérico XAML usos do WPF".  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [Extensão de marcação x:Type](x-type-markup-extension.md)
- [Tipos inseridos para primitivos de linguagem XML comuns](built-in-types-for-common-xaml-language-primitives.md)
- [Genéricos em XAML](generics-in-xaml.md)
