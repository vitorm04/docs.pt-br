---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071531"
---
# <a name="xfactorymethod-directive"></a>Diretiva x:FactoryMethod
Especifica um método diferente de um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver seu tipo de backup.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Uso de atributo XAML, sem x:Argumentos  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Uso de atributo XAML, x:Argumentos como Elemento(s)  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`methodname`|O nome do método de string de um método que os `object`processadores XAML chamam para inicializar a instância especificada como . Consulte Observações.|  
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto para objetos que especificam parâmetros do método de fábrica. A ordem é significativa; significa a ordem em que os argumentos devem ser passados para o método de fábrica.|  
  
## <a name="remarks"></a>Comentários  
 Se `methodname` é um método de instância, não pode ser qualificado.  
  
 Métodos estáticos como métodos de fábrica são suportados. Se `methodname` é um `methodname` método estático, `typeName.methodName` é `typeName` fornecido como uma combinação, onde nomeia a classe que define o método de fábrica estático. `typeName`pode ser qualificado por prefixo se se referir a um tipo em um xmlns mapeado. `typeName`pode ser um `typeof(object)`tipo diferente de .  
  
 O método de fábrica deve ser um método público declarado do tipo que apoia o elemento objeto relevante.  
  
 O método de fábrica deve retornar uma instância que seja atribuída ao objeto relevante. Os métodos de fábrica nunca devem retornar nulos.  
  
 `x:Arguments`opera em um princípio de melhor correspondência para assinaturas de métodos de fábrica. A correspondência avalia a contagem de parâmetros primeiro. Se houver mais de uma possível correspondência para uma contagem de parâmetros, o tipo de parâmetro é então avaliado e a melhor correspondência é determinada. Se ainda houver ambiguidade após essa fase de avaliação, o comportamento do processador XAML é indefinido.  
  
 O `x:FactoryMethod` uso do elemento não é o uso do elemento de propriedade no sentido típico, porque a marcação diretiva não faz referência ao tipo do elemento objeto que contém. Espera-se que o uso do elemento seja menos comum do que o uso de atributos. `x:Arguments`(uso de atributo ou elemento) `x:FactoryMethod` pode ser usado juntamente com o uso do elemento, mas isso não é mostrado especificamente nas seções de uso.  
  
 `x:FactoryMethod`como um elemento deve preceder quaisquer `x:Arguments` outros elementos de propriedade, deve preceder qualquer também fornecido como elementos, e deve preceder qualquer texto/texto interno/inicialização.  
  
## <a name="see-also"></a>Confira também

- [Diretiva x:Arguments](xarguments-directive.md)
