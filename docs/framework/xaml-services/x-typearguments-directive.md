---
title: Diretiva x:TypeArguments
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: "18"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e601fb5895460e52aa21836c542d0b1367527f09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xtypearguments-directive"></a>Diretiva x:TypeArguments
Passa para a restrição de tipo de argumentos de um genérico para o construtor do tipo genérico.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`object`|Uma declaração de elemento de objeto de um tipo XAML, que é apoiado por um tipo genérico do CLR. Se `object` se refere a um tipo XAML que não seja o padrão do namespace de XAML, `object` requer um prefixo para indicar o namespace XAML onde `object` existe.|  
|`typeString`|Uma cadeia de caracteres que declara um ou mais XAML Digite nomes como cadeias de caracteres, que fornece os argumentos de tipo para o tipo genérico do CLR. Consulte comentários para obter notas de sintaxe adicional.|  
  
## <a name="remarks"></a>Comentários  
 Na maioria dos casos, os tipos XAML que são usados como um item de informação em um `typeString` cadeia de caracteres são prefixados. Tipos típicos de restrições genéricas do CLR (por exemplo, <xref:System.Int32> e <xref:System.String>) provenientes de bibliotecas de classe base do CLR. Essas bibliotecas não são mapeados para típico padrão de específica da estrutura XAML namespaces e, portanto, exigem um mapeamento de prefixo para uso em XAML.  
  
 Você pode especificar mais de um nome de tipo XAML usando um delimitador de vírgula.  
  
 Se as restrições genéricas se usam tipos genéricos, os argumentos de tipo aninhado de restrição podem ser contidos por parênteses ().  
  
 Observe que essa definição de `x:TypeArguments` é específico para serviços XAML do .NET Framework e usando o backup do CLR. Uma definição de nível de linguagem que pode ser encontrada na [ \[XAML MS\] seção 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Exemplos de uso  
 Para esses exemplos, suponha que as seguintes definições do namespace XAML são declaradas:  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Lista\<cadeia de caracteres >  
 `<scg:List x:TypeArguments="sys:String" ...>`cria um novo <xref:System.Collections.Generic.List%601> com um <xref:System.String> argumento de tipo.  
  
### <a name="dictionarystringstring"></a>Dicionário\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`cria um novo <xref:System.Collections.Generic.Dictionary%602> com dois <xref:System.String> argumentos de tipo.  
  
### <a name="queuekeyvaluepairstringstring"></a>Fila < KeyValuePair\<cadeia de caracteres, cadeia de caracteres >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`cria um novo <xref:System.Collections.Generic.Queue%601> que tem uma restrição de <xref:System.Collections.Generic.KeyValuePair%602> com os argumentos de tipo de restrição interna <xref:System.String> e <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Usos XAML genérico 2006 XAML e WPF  
 Para uso de 2006 XAML e XAML que é usado para aplicativos do WPF, existem as seguintes restrições para `x:TypeArguments` e usos de tipo genérico do XAML em geral:  
  
-   Apenas o elemento raiz de um arquivo XAML pode dar suporte a um uso XAML genérico que faz referência a um tipo genérico.  
  
-   O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>. As funções de página são o cenário principal para o suporte de uso genérico de XAML no WPF.  
  
-   O elemento raiz elemento XAML objeto genérica também deverá declarar uma classe parcial usando `x:Class`. Isso é verdadeiro mesmo se a ação de compilação definindo um WPF.  
  
-   `x:TypeArguments`não é possível fazer referência a restrições genéricas aninhadas.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou 2006 de XAML sem WPF 3.0 ou 3.5 do WPF dependência  
 Em serviços de XAML .NET Framework para 2006 XAML ou XAML 2009, as restrições relacionadas a WPF no uso XAML genérico são reduzidas. Você pode instanciar um elemento de objeto genérico em qualquer posição na marcação XAML que o modelo de objeto e o sistema de tipo backup pode dar suporte.  
  
 Se você usar o XAML 2009 em vez de mapeamento do CLR base tipos para obter tipos XAML para primitivos de linguagem comum, você pode usar [tipos internos para primitivos de linguagem XAML comum](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) como itens de informações em um `typeString`. Por exemplo, você pode declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o namespace XAML linguagem XAML XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 No WPF e direcionamento [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar recursos XAML 2009 junto com `x:TypeArguments` , mas apenas para XAML livre (XAML não marcação-compilado). Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009. Se você precisa para marcação de compilar o XAML, você deve operam sob as restrições na seção "XAML 2006 e WPF genérica usos de XAML".  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Class](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Extensão de marcação x:Type](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Tipos inseridos para primitivos de linguagem XML comuns](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [Genéricos em XAML](../../../docs/framework/xaml-services/generics-in-xaml.md)
