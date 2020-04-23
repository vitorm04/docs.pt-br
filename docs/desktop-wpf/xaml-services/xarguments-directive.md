---
title: Diretiva x:Arguments
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071587"
---
# <a name="xarguments-directive"></a>Diretiva x:Arguments

Embala argumentos de construção para uma declaração de elemento de objeto construtor não parâmetro no XAML ou para uma declaração de objeto de método de fábrica.

## <a name="xaml-element-usage-nonparameterless-constructor"></a>Uso do elemento XAML (construtor sem parâmetro)

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a>Uso do elemento XAML (método de fábrica)

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto que especificam argumentos a serem passados para o construtor ou método de fábrica não-parâmetro sem parâmetros de apoio.<br /><br /> O uso típico é usar o texto de inicialização dentro dos elementos do objeto para especificar os valores reais do argumento. Veja a seção Exemplos.<br /><br /> A ordem dos elementos é significativa. Os tipos XAML em ordem devem corresponder aos tipos e ordem de tipo da sobrecarga do construtor de apoio ou do método de fábrica.|
|`methodName`|O nome do método de `x:Arguments` fábrica que deve processar quaisquer argumentos.|

## <a name="dependencies"></a>Dependências

`x:FactoryMethod`pode modificar o escopo `x:Arguments` e o comportamento quando se aplica.

Se `x:FactoryMethod` não for `x:Arguments` especificado, aplica-se a assinaturas alternativas (não padrão) dos construtores de apoio.

Se `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a uma sobrecarga do método nomeado.

## <a name="remarks"></a>Comentários

XAML 2006 pode suportar inicialização não padrão através de texto de inicialização. No entanto, a aplicação prática de uma técnica de construção de texto de inicialização é limitada. O texto de inicialização é tratado como uma única seqüência de texto; portanto, ele só adiciona capacidade para uma inicialização de parâmetro único, a menos que um conversor de tipo seja definido para o comportamento de construção que pode analisar itens de informações personalizadas e delimitadores personalizados da string. Além disso, a seqüência de texto para a lógica do objeto é potencialmente um determinado conversor padrão padrão do analisador XAML para manusear primitivos que não seja uma seqüência de string verdadeira.

O `x:Arguments` uso do XAML não é o uso do elemento de propriedade no sentido típico, porque a marcação diretiva não faz referência ao tipo do elemento do objeto que contém. É mais parecido com outras `x:Code` diretivas, como quando o elemento demarca um intervalo no qual a marcação deve ser interpretada como diferente do padrão para o conteúdo infantil. Neste caso, o tipo XAML de cada elemento objeto comunica informações sobre os tipos de argumento, que são usados por analisadores XAML para determinar qual método específico de fábrica de construção um `x:Arguments` uso está tentando referenciar.

`x:Arguments`para que um elemento objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou seqüências de inicialização do elemento objeto. Os elementos `x:Arguments` do objeto dentro podem incluir atributos e seqüências de inicialização, conforme permitido por esse tipo XAML e seu método de construção ou fábrica de apoio. Para o objeto ou os argumentos, você pode especificar tipos XAML personalizados ou tipos XAML que estão fora do namespace XAML padrão, fazendo referência a mapeamentos de prefixos estabelecidos.

Os processadores XAML usam as seguintes diretrizes `x:Arguments` para determinar como os argumentos especificados devem ser usados para construir um objeto. Se `x:FactoryMethod` for especificado, as informações `x:FactoryMethod` serão comparadas `x:FactoryMethod` com as especificadas (observe que o valor é o nome do método, e o método nomeado pode ter sobrecargas. Se `x:FactoryMethod` não for especificado, as informações são comparadas com o conjunto de todas as sobrecargas de construtores públicos do objeto. A lógica de processamento XAML então compara o número de parâmetros e seleciona a sobrecarga com a aridade correspondente. Se houver mais de uma correspondência, o processador XAML deve comparar os tipos de parâmetros baseados nos tipos XAML dos elementos do objeto fornecidos. Se ainda houver mais de uma correspondência, o comportamento do processador XAML é indefinido. Se `x:FactoryMethod` um for especificado, mas o método não puder ser resolvido, um processador XAML deve abrir uma exceção.

Um uso `<x:Arguments>string</x:Arguments>` de atributo XAML é tecnicamente possível. No entanto, isso não fornece recursos além do que poderia ser feito de outra forma através de texto de inicialização e conversores de tipo, e usar essa sintaxe não é a intenção de design dos recursos do método de fábrica XAML 2009.

## <a name="examples"></a>Exemplos

O exemplo a seguir mostra uma assinatura de construtor não-parâmetro, em seguida, o uso XAML dessa `x:Arguments` assinatura.

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

O exemplo a seguir mostra uma assinatura de método `x:Arguments` de fábrica de destino, em seguida, o uso XAML de que acessa essa assinatura.

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a>Confira também

- [Definir tipos personalizados para uso com os serviços XAML do .NET](define-custom-types.md)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
