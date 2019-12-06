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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837188"
---
# <a name="xtypearguments-directive"></a>Diretiva x:TypeArguments
Passa a restringir os argumentos de tipo de um genérico para o construtor do tipo genérico.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`object`|Uma declaração de elemento de objeto de um tipo XAML, que é apoiada por um tipo genérico CLR. Se `object` se refere a um tipo XAML que não é do namespace XAML padrão, `object` requer um prefixo para indicar o namespace XAML onde `object` existe.|  
|`typeString`|Uma cadeia de caracteres que declara um ou mais nomes de tipo XAML como cadeias de caracteres, que fornece os argumentos de tipo para o tipo genérico CLR. Consulte comentários para ver as notas de sintaxe adicionais.|  
  
## <a name="remarks"></a>Comentários  
 Na maioria dos casos, os tipos XAML que são usados como um item de informações em uma cadeia de caracteres `typeString` são prefixados. Tipos típicos de restrições genéricas do CLR (por exemplo, <xref:System.Int32> e <xref:System.String>) vêm de bibliotecas de classes base do CLR. Essas bibliotecas não são mapeadas para namespaces padrão XAML específicos da estrutura e, portanto, exigem um mapeamento de prefixo para o uso do XAML.  
  
 Você pode especificar mais de um nome de tipo XAML usando um delimitador de vírgula.  
  
 Se as próprias restrições genéricas usarem tipos genéricos, os argumentos de tipo de restrição aninhada poderão ser contidos por parênteses ().  
  
 Observe que essa definição de `x:TypeArguments` é específica para .NET Framework serviços XAML e o uso de backup do CLR. Uma definição de nível de idioma pode ser encontrada em [\[MS-XAML\] seção 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="usage-examples"></a>Exemplos de uso  
 Para esses exemplos, suponha que as seguintes definições de namespace XAML sejam declaradas:  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Listar\<cadeia de caracteres >  
 `<scg:List x:TypeArguments="sys:String" ...>` instancia um novo <xref:System.Collections.Generic.List%601> com um argumento de tipo <xref:System.String>.  
  
### <a name="dictionarystringstring"></a>\<de cadeia de caracteres de dicionário, Cadeia de caracteres >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instancia um novo <xref:System.Collections.Generic.Dictionary%602> com dois argumentos de tipo <xref:System.String>.  
  
### <a name="queuekeyvaluepairstringstring"></a>Queue < KeyValuePair\<String, Cadeia de caracteres > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instancia uma nova <xref:System.Collections.Generic.Queue%601> que tem uma restrição de <xref:System.Collections.Generic.KeyValuePair%602> com os argumentos de tipo de restrição interna <xref:System.String> e <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Usos de XAML genérico XAML 2006 e WPF  
 Para o uso de XAML 2006 e XAML que é usado para aplicativos do WPF, existem as seguintes restrições para `x:TypeArguments` e usos de tipo genérico do XAML em geral:  
  
- Somente o elemento raiz de um arquivo XAML pode dar suporte a um uso de XAML genérico que faz referência a um tipo genérico.  
  
- O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>. As funções de página são o principal cenário para suporte de uso genérico XAML no WPF.  
  
- O elemento de objeto XAML do elemento raiz para o genérico também deve declarar uma classe parcial usando `x:Class`. Isso é verdadeiro mesmo se definir uma ação de compilação do WPF.  
  
- `x:TypeArguments` não pode referenciar restrições genéricas aninhadas.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou XAML 2006 sem nenhuma dependência do WPF 3,0 ou do WPF 3,5  
 Em .NET Framework serviços XAML para XAML 2006 ou XAML 2009, as restrições relacionadas ao WPF no uso de XAML genérico são relaxadas. Você pode criar uma instância de um elemento de objeto genérico em qualquer posição na marcação XAML que o sistema de tipo de backup e o modelo de objeto podem dar suporte.  
  
 Se você usar o XAML 2009 em vez de mapear os tipos de base do CLR para obter tipos XAML para primitivos de linguagem comum, poderá usar [tipos internos para primitivos comuns de linguagem XAML](built-in-types-for-common-xaml-language-primitives.md) como itens de informações em um `typeString`. Por exemplo, você pode declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o namespace XAML da linguagem XAML para XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 No WPF e, ao direcionar .NET Framework 4, você pode usar os recursos do XAML 2009 juntamente com `x:TypeArguments`, mas apenas para XAML livre (XAML que não é compilado por marcação). O XAML com compilação de marcação para WPF e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos do XAML 2009. Se você precisar compilar a marcação do XAML, você deve operar sob as restrições indicadas na seção "XAML 2006 e usos genéricos XAML do WPF".  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [Extensão de marcação x:Type](x-type-markup-extension.md)
- [Tipos inseridos para primitivos de linguagem XML comuns](built-in-types-for-common-xaml-language-primitives.md)
- [Genéricos em XAML](generics-in-xaml.md)
