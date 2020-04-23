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
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071349"
---
# <a name="xtypearguments-directive"></a>Diretiva x:TypeArguments

Passa argumentos de tipo restritivas de um genérico para o construtor do tipo genérico.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`object`|Uma declaração de elemento de objeto de um tipo XAML, que é apoiada por um tipo genérico CLR. Se `object` se refere a um tipo XAML que não é `object` do espaço de nome XAML `object` padrão, requer um prefixo para indicar o namespace XAML onde existe.|
|`typeString`|Uma string que declara um ou mais nomes de tipo XAML como strings, que fornece os argumentos do tipo para o tipo genérico CLR. Consulte observações para obter notas adicionais de sintaxe.|

## <a name="remarks"></a>Comentários

Na maioria dos casos, os tipos XAML que `typeString` são usados como item de informação em uma seqüência são prefixados. Os tipos típicos de restrições <xref:System.Int32> genéricas clr (por exemplo, e <xref:System.String>) vêm de bibliotecas de classe base clr. Essas bibliotecas não são mapeadas para espaços de nomes XAML padrão específicos da estrutura e, portanto, exigem um mapeamento de prefixo para o uso do XAML.

Você pode especificar mais de um nome de tipo XAML usando um delimitador de comma.

Se as próprias restrições genéricas usarem tipos genéricos, os argumentos do tipo de restrição aninhada podem ser contidos por parênteses ().

Observe que essa `x:TypeArguments` definição é específica para .NET XAML Services e usando o backup CLR. Uma definição de nível de idioma pode ser encontrada na [ \[Seção 5.3.11 do MS-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="usage-examples"></a>Exemplos de uso

Para esses exemplos, suponha que as seguintes definições de namespace XAML sejam declaradas:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>>\<de seqüência de cordas de lista

`<scg:List x:TypeArguments="sys:String" ...>`instancia um <xref:System.Collections.Generic.List%601> novo <xref:System.String> com um argumento de tipo.

### <a name="dictionarystringstring"></a>String\<do dicionário,> de cordas

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`instancia um <xref:System.Collections.Generic.Dictionary%602> novo <xref:System.String> com dois argumentos de tipo.

### <a name="queuekeyvaluepairstringstring"></a>Fila<string\<KeyValuePair,String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`instancia um <xref:System.Collections.Generic.Queue%601> novo que <xref:System.Collections.Generic.KeyValuePair%602> tem uma restrição de <xref:System.String> <xref:System.String>com os argumentos do tipo de restrição interna e .

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 e WPF Genéricos Usos XAML

Para o uso de XAML 2006 e XAML que é usado `x:TypeArguments` para aplicações WPF, existem as seguintes restrições para e usos genéricos do tipo de XAML em geral:

- Apenas o elemento raiz de um arquivo XAML pode suportar um uso genérico de XAML que faz referência a um tipo genérico.

- O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>. As funções da página são o cenário principal para o suporte de uso genérico XAML no WPF.

- O elemento raiz elemento xaml elemento para o `x:Class`genérico também deve declarar uma classe parcial usando . Isso é verdade mesmo se definir uma ação de construção wpf.

- `x:TypeArguments`não pode referenciar restrições genéricas aninhadas.

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou XAML 2006 sem dependência wpf 3.0 ou WPF 3.5

Em Serviços XAML .NET para XAML 2006 ou XAML 2009, as restrições relacionadas ao WPF sobre o uso genérico de XAML são relaxadas. Você pode instanciar um elemento de objeto genérico em qualquer posição na marcação XAML que o sistema de tipo de backup e o modelo de objeto podem suportar.

Se você usar o XAML 2009 em vez de mapear os tipos de base clr para obter tipos XAML para primitivos de `typeString`linguagem comum, você pode usar [tipos incorporados para primitivos comuns da linguagem XAML](types-for-primitives.md) como itens de informação em um . Por exemplo, você pode declarar o seguinte (mapeamentos de prefixo não mostrados, mas x é o espaço de nome XAML da linguagem XAML para XAML 2009):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

No WPF e ao direcionar o .NET Framework 4 ou o .NET Core 3.0 (ou `x:TypeArguments` posterior), você pode usar os recursos do XAML 2009 em conjunto com, mas apenas para XAML solto (XAML que não é compilado por marcação). O XAML compilado por marcação para WPF e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do XAML 2009. Se você precisar marcar a compilação do XAML, você deve operar sob as restrições anotadas na seção [XAML 2006 e WPF Generic XAML Usages.](#xaml-2006-and-wpf-generic-xaml-usages) O BAML só é suportado no .NET Framework.

## <a name="see-also"></a>Confira também

- [Diretiva x:Class](xclass-directive.md)
- [Extensão de marcação x:Type](xtype-markup-extension.md)
- [Tipos inseridos para primitivos de linguagem XML comuns](types-for-primitives.md)
- [Genéricos em XAML](generics.md)
