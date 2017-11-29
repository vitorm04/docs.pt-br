---
title: Diretiva x:Arguments
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 00f605bba709f0ce5f3238ccc3c6ac6cd962f0a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xarguments-directive"></a>Diretiva x:Arguments
Argumentos de construção de pacotes para uma declaração de elemento de objeto do construtor não-padrão em XAML ou para uma declaração de objeto do método de fábrica.  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>Uso do elemento XAML (construtor de não-padrão)  
  
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
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto que especifica os argumentos a serem passados para o método de construtor ou fábrica de não-padrão do backup.<br /><br /> Uso típico é usar o texto de inicialização em elementos de objeto para especificar os valores de argumento real. Consulte a seção exemplos.<br /><br /> A ordem dos elementos é significativa. Os tipos XAML em ordem devem corresponder aos tipos e digite ordem da sobrecarga de método de construtor ou fábrica de backup.|  
|`methodName`|O nome do método de fábrica que deve processar qualquer `x:Arguments` argumentos.|  
  
## <a name="dependencies"></a>Dependências  
 `x:FactoryMethod`pode modificar o escopo e o comportamento onde `x:Arguments` se aplica.  
  
 Se nenhum `x:FactoryMethod` for especificado, `x:Arguments` se aplica às assinaturas de (não-padrão) alternativas dos construtores de backup.  
  
 Se `x:FactoryMethod` for especificado, `x:Arguments` aplica-se a uma sobrecarga do método nomeado.  
  
## <a name="remarks"></a>Comentários  
 2006 XAML pode dar suporte a inicialização não padrão por meio do texto de inicialização. No entanto, a aplicação de prática de uma técnica de construção de texto de inicialização é limitada. Texto de inicialização é tratado como uma cadeia de caracteres de texto simples; Portanto, ele apenas adiciona o recurso para a inicialização de um único parâmetro, a menos que um conversor de tipo está definido para o comportamento de construção que pode analisar os itens de informações personalizadas e delimitadores personalizados da cadeia de. Além disso, a cadeia de caracteres de texto à lógica do objeto é potencialmente conversor de tipo de um determinado XAML analisador padrão de nativo para lidar com primitivos diferente de uma cadeia de caracteres.  
  
 O `x:Arguments` uso XAML não é uso de elemento de propriedade no sentido típico, porque a marcação de diretiva não faz referência a tipo de elemento de objeto que contém. Ele é mais semelhante a outras diretivas como `x:Code` onde o elemento determina um intervalo no qual a marcação deve ser interpretada como diferente do padrão para o conteúdo filho. Nesse caso, o tipo de XAML de cada elemento do objeto se comunica informações sobre os tipos de argumento, que são usadas pelo analisadores XAML para determinar qual método de fábrica construtor específico assinatura um `x:Arguments` uso está tentando fazer referência.  
  
 `x:Arguments`para um elemento de objeto que está sendo construído deve preceder quaisquer outros elementos de propriedade, conteúdo, texto interno ou cadeias de caracteres de inicialização do elemento de objeto. Os elementos de objeto dentro de `x:Arguments` podem incluir atributos e cadeias de caracteres de inicialização, conforme permitido pelo tipo XAML e seu método de construtor ou fábrica de backup. Para o objeto ou os argumentos, você pode especificar os tipos XAML personalizados ou tipos XAML que estiverem fora do namespace XAML padrão referenciando mapeamentos de prefixo estabelecida.  
  
 Processadores XAML usam as diretrizes a seguir para determinar como os argumentos especificados em `x:Arguments` deve ser usado para construir um objeto. Se `x:FactoryMethod` for especificado, as informações são comparadas especificado `x:FactoryMethod` (Observe que o valor de `x:FactoryMethod` é o nome do método e o método nomeado pode ter sobrecargas. Se `x:FactoryMethod` não for especificado, as informações são comparadas ao conjunto de todas as sobrecargas de construtor público do objeto. Lógica de processamento de XAML, em seguida, compara o número de parâmetros e seleciona a sobrecarga com arity correspondente. Se houver mais de uma correspondência, o processador XAML compare os tipos dos parâmetros com base nos tipos de XAML dos elementos de objeto fornecido. Se houver ainda mais de uma correspondência, o comportamento de processador do XAML é indefinido. Se um `x:FactoryMethod` for especificado, mas o método não pode ser resolvido, um processador XAML deve lançar uma exceção.  
  
 Um uso do atributo XAML `<x:Arguments>string</x:Arguments>` é tecnicamente possível. No entanto, isso não fornece recursos além do que pode ser feito caso contrário pelo conversores de texto e o tipo de inicialização e usar essa sintaxe não é a intenção de design dos recursos do método de fábrica do XAML 2009.  
  
## <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra um construtor não padrão de assinatura e, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.  
  
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
  
 O exemplo a seguir mostra uma assinatura de método da fábrica de destino, em seguida, o uso XAML de `x:Arguments` que acessa essa assinatura.  
  
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
 [Definindo tipos personalizados para uso com serviços XAML do .NET Framework](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
