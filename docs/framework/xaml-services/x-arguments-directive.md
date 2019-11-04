---
title: Diretiva x:Arguments
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458658"
---
# <a name="xarguments-directive"></a>Diretiva x:Arguments
Argumentos de construção de pacotes para uma declaração de elemento de objeto de construtor sem parâmetros em XAML ou para uma declaração de objeto de método de fábrica.  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>Uso do elemento XAML (Construtor sem parâmetros)  
  
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
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto que especificam argumentos a serem passados para o construtor não sem parâmetros ou para o método de fábrica.<br /><br /> O uso típico é usar o texto de inicialização dentro dos elementos de objeto para especificar os valores de argumento reais. Consulte a seção de exemplos.<br /><br /> A ordem dos elementos é significativa. Os tipos XAML na ordem devem corresponder aos tipos e à ordem de tipo do construtor de suporte ou sobrecarga de método de fábrica.|  
|`methodName`|O nome do método de fábrica que deve processar os argumentos de `x:Arguments`.|  
  
## <a name="dependencies"></a>Dependências  
 `x:FactoryMethod` pode modificar o escopo e o comportamento onde `x:Arguments` se aplica.  
  
 Se nenhum `x:FactoryMethod` for especificado, `x:Arguments` se aplicará a assinaturas alternativas (não padrão) dos construtores de backup.  
  
 Se `x:FactoryMethod` for especificado, `x:Arguments` se aplicará a uma sobrecarga do método nomeado.  
  
## <a name="remarks"></a>Comentários  
 O XAML 2006 pode dar suporte à inicialização não padrão por meio de texto de inicialização. No entanto, o aplicativo prático de uma técnica de construção de texto de inicialização é limitado. O texto de inicialização é tratado como uma única cadeia de texto; Portanto, ele só adiciona recursos para uma única inicialização de parâmetro, a menos que um conversor de tipo seja definido para o comportamento de construção que possa analisar itens de informações personalizados e delimitadores personalizados da cadeia de caracteres. Além disso, a cadeia de caracteres de texto para lógica de objeto é potencialmente um conversor de tipo padrão nativo do analisador XAML para manipular primitivos diferentes de uma cadeia de caracteres verdadeira.  
  
 O uso `x:Arguments` XAML não é o uso do elemento de propriedade no sentido típico, porque a marcação da diretiva não faz referência ao tipo do elemento de objeto recipiente. Ele é mais semelhante a outras diretivas, como `x:Code` onde o elemento marca um intervalo no qual a marcação deve ser interpretada como diferente do padrão para conteúdo filho. Nesse caso, o tipo XAML de cada elemento Object comunica informações sobre os tipos de argumentos, que é usado por analisadores XAML para determinar qual assinatura de método de fábrica de Construtor específica um uso de `x:Arguments` está tentando referenciar.  
  
 `x:Arguments` para um elemento de objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou cadeias de inicialização do elemento Object. Os elementos de objeto dentro de `x:Arguments` podem incluir atributos e cadeias de caracteres de inicialização, conforme permitido pelo tipo XAML e seu construtor de suporte ou método de fábrica. Para o objeto ou os argumentos, você pode especificar tipos XAML personalizados ou tipos XAML que, de outra forma, estão fora do namespace XAML padrão referenciando mapeamentos de prefixo estabelecidos.  
  
 Os processadores XAML usam as seguintes diretrizes para determinar como os argumentos especificados em `x:Arguments` devem ser usados para construir um objeto. Se `x:FactoryMethod` for especificado, as informações serão comparadas com o `x:FactoryMethod` especificado (Observe que o valor de `x:FactoryMethod` é o nome do método e o método nomeado pode ter sobrecargas. Se `x:FactoryMethod` não for especificado, as informações serão comparadas ao conjunto de todas as sobrecargas de construtor público do objeto. Em seguida, a lógica de processamento XAML compara o número de parâmetros e seleciona a sobrecarga com arity correspondente. Se houver mais de uma correspondência, o processador XAML deve comparar os tipos dos parâmetros com base nos tipos XAML dos elementos de objeto fornecidos. Se ainda houver mais de uma correspondência, o comportamento do processador XAML será indefinido. Se um `x:FactoryMethod` for especificado, mas o método não puder ser resolvido, um processador XAML deverá lançar uma exceção.  
  
 Um `<x:Arguments>string</x:Arguments>` de uso de atributo XAML é tecnicamente possível. No entanto, isso não fornece recursos além do que poderia ser feito de outra forma por meio de texto de inicialização e conversores de tipo, e usar essa sintaxe não é a intenção de design dos recursos de método de fábrica do XAML 2009.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra uma assinatura de construtor sem parâmetros e, em seguida, o uso do XAML de `x:Arguments` que acessa essa assinatura.  
  
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
  
 O exemplo a seguir mostra uma assinatura de método de fábrica de destino e, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Definindo tipos personalizados para uso com serviços XAML do .NET Framework](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [Visão geral de XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
