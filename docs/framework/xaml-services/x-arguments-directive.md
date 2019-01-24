---
title: Diretiva x:Arguments
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: d4cff4c2f95d1418371921a3ac992a3b243d1c07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490811"
---
# <a name="xarguments-directive"></a>Diretiva x:Arguments
Argumentos de construção de pacotes para uma declaração de elemento de objeto de construtor não padrão no XAML ou para uma declaração de objeto do método de fábrica.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>Uso do elemento XAML (construtor não padrão)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>Uso do elemento XAML (método de fábrica)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto que especifica argumentos a serem passados para o método de construtor ou fábrica de não-padrão do suporte.<br /><br /> Uso típico é usar o texto de inicialização dentro de elementos de objeto para especificar os valores de argumento real. Consulte a seção de exemplos.<br /><br /> A ordem dos elementos é significativa. Os tipos XAML na ordem devem correspondem aos tipos e digite a ordem da sobrecarga de método de construtor ou fábrica fazendo backup.|  
|`methodName`|O nome do método de fábrica que deve processar qualquer `x:Arguments` argumentos.|  
  
## <a name="dependencies"></a>Dependências  
 `x:FactoryMethod` pode modificar o escopo e o comportamento em que `x:Arguments` se aplica.  
  
 Se nenhum `x:FactoryMethod` for especificado, `x:Arguments` se aplica a assinaturas de alternativas (não-padrão) dos construtores de backup.  
  
 Se `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a uma sobrecarga do método nomeado.  
  
## <a name="remarks"></a>Comentários  
 XAML 2006 pode dar suporte a inicialização por meio do texto de inicialização não padrão. No entanto, a aplicação prática de uma técnica de construção de texto de inicialização é limitada. Texto de inicialização é tratado como uma cadeia de caracteres de texto simples; Portanto, ele apenas adiciona funcionalidade para a inicialização de um único parâmetro, a menos que um conversor de tipo é definido para o comportamento de construção que pode analisar itens de informações personalizadas e delimitadores personalizados da cadeia de caracteres. Além disso, a cadeia de caracteres de texto à lógica do objeto é potencialmente conversor de tipo de um analisador XAML determinado padrão de nativo para lidar com primitivos que não seja uma cadeia de caracteres.  
  
 O `x:Arguments` uso XAML não é uso do elemento de propriedade no sentido de típico, porque a marcação de diretiva não faz referência a tipo de elemento de objeto recipiente. Ele é mais semelhante de outras diretivas como `x:Code` onde o elemento delimita um intervalo no qual a marcação deve ser interpretada como diferente do padrão para o conteúdo filho. Nesse caso, o tipo XAML de cada elemento de objeto se comunica informações sobre os tipos de argumento, que são usadas pelo analisadores XAML para determinar qual assinatura do método de fábrica construtor específico um `x:Arguments` uso está tentando fazer referência.  
  
 `x:Arguments` para um elemento de objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou cadeias de caracteres de inicialização do elemento de objeto. Os elementos de objeto dentro de `x:Arguments` podem incluir atributos e cadeias de caracteres de inicialização, conforme permitido por esse tipo XAML e seu método de construtor ou fábrica de backup. Para o objeto ou os argumentos, você pode especificar os tipos XAML personalizados ou tipos XAML que estariam fora do namespace XAML padrão, fazendo referência a mapeamentos de prefixo estabelecido.  
  
 Processadores XAML usam as diretrizes a seguir para determinar como os argumentos especificados no `x:Arguments` deve ser usado para construir um objeto. Se `x:FactoryMethod` for especificado, em comparação com informações especificado `x:FactoryMethod` (Observe que o valor de `x:FactoryMethod` é o nome do método e o método nomeado pode ter sobrecargas. Se `x:FactoryMethod` não for especificado, informações é comparado com o conjunto de todas as sobrecargas de construtor público do objeto. Lógica de processamento de XAML, em seguida, compara o número de parâmetros e seleciona a sobrecarga com arity correspondente. Se houver mais de uma correspondência, o processador XAML deve comparar os tipos dos parâmetros com base nos tipos XAML dos elementos de objeto fornecido. Se não houver ainda mais de uma correspondência, o comportamento do processador XAML é indefinido. Se um `x:FactoryMethod` for especificado, mas o método não pode ser resolvido, um processador XAML deve lançar uma exceção.  
  
 Um uso do atributo XAML `<x:Arguments>string</x:Arguments>` é tecnicamente possível. No entanto, isso não fornece recursos além do que poderia ser feito caso contrário, por meio de conversores de texto e o tipo de inicialização e usar essa sintaxe não é a intenção de design dos recursos do método de fábrica do XAML 2009.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra um construtor não padrão, assinatura e, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.  
  
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
  
 O exemplo a seguir mostra uma assinatura de método de fábrica de destino, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.  
  
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
- [Definindo tipos personalizados para uso com serviços XAML do .NET Framework](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
