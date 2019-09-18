---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053784"
---
# <a name="xfactorymethod-directive"></a>Diretiva x:FactoryMethod
Especifica um método diferente de um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver seu tipo de apoio.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Uso de atributo XAML, sem x:Arguments  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Uso de atributo XAML, x:Arguments como elemento (s)  
  
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
|`methodname`|O nome do método de cadeia de caracteres de um método que os processadores XAML chamam para `object`inicializar a instância especificada como. Consulte Observações.|  
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto para objetos que especificam parâmetros de método de fábrica. A ordem é significativa; significa a ordem na qual os argumentos devem ser passados para o método de fábrica.|  
  
## <a name="remarks"></a>Comentários  
 Se `methodname` for um método de instância, ele não poderá ser qualificado.  
  
 Há suporte para métodos estáticos como métodos de fábrica. Se `methodname` é um método estático, `methodname` é fornecido como um *TypeName*. *methodName* a combinação, em que *TypeName* nomeia a classe que define o método de alocador estático. *TypeName* pode ser qualificado por prefixo se fizer referência a um tipo em um xmlns mapeado. *TypeName* pode ser um tipo diferente de `typeof(object)`.  
  
 O método de fábrica deve ser um método público declarado do tipo que faz o backup do elemento de objeto relevante.  
  
 O método de fábrica deve retornar uma instância que pode ser atribuída ao objeto relevante. Os métodos de fábrica nunca devem retornar NULL.  
  
 `x:Arguments`Opera em um princípio de melhor correspondência para assinaturas de métodos de fábrica. A correspondência avalia a contagem de parâmetros primeiro. Se houver mais de uma correspondência possível para uma contagem de parâmetros, o tipo de parâmetro será avaliado e a melhor correspondência será determinada. Se ainda houver ambigüidade após esta fase de avaliação, o comportamento do processador XAML será indefinido.  
  
 O `x:FactoryMethod` uso do elemento não é o uso do elemento de propriedade no sentido típico, porque a marcação da diretiva não faz referência ao tipo do elemento de objeto recipiente. Espera-se que o uso do elemento seja menos comum do que o uso do atributo. `x:Arguments`(o atributo ou uso do elemento) pode ser usado junto `x:FactoryMethod` com o uso do elemento, mas isso não é mostrado especificamente nas seções de uso.  
  
 `x:FactoryMethod`como um elemento deve preceder quaisquer outros elementos de propriedade, deve preceder quaisquer `x:Arguments` também fornecidos como elementos e deve preceder qualquer texto de conteúdo/texto interno/inicialização.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Arguments](x-arguments-directive.md)
