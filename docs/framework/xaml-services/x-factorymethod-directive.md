---
title: Diretiva x:FactoryMethod
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 436caa9b93467dcf2a0763bcc0962a2beb722315
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972014"
---
# <a name="xfactorymethod-directive"></a>Diretiva x:FactoryMethod
Especifica um método que não seja um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver o seu tipo de backup.  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>Uso do atributo XAML, não há argumentos de x:  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>Uso do atributo XAML, x: argumentos como elemento (s)  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`methodname`|O nome do método de cadeia de caracteres de um método que processadores XAML chamar para inicializar a instância especificada como `object`. Consulte Observações.|  
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto para objetos que especificam parâmetros de método de fábrica. A ordem é significativa; Isso significa que a ordem na qual os argumentos devem ser passados para o método de fábrica.|  
  
## <a name="remarks"></a>Comentários  
 Se `methodname` é um método de instância, ele não pode ser qualificado.  
  
 Há suporte para métodos estáticos como métodos de fábrica. Se `methodname` é um método estático, `methodname` é fornecido como um *typeName*. *methodName* combinação, onde *typeName* nomeia a classe que define o método de fábrica estáticos. *typeName* pode ser qualificado prefixo se referindo-se a um tipo em um xmlns mapeado. *typeName* pode ser um tipo diferente `typeof(object)`.  
  
 O método de fábrica deve ser um método público declarado do tipo que sustenta o elemento de objeto relevante.  
  
 O método de fábrica deve retornar uma instância que pode ser atribuído ao objeto relevante. Métodos de fábrica nunca devem retornar nulos.  
  
 `x:Arguments` opera em um princípio da melhor correspondência para assinaturas de métodos de fábrica. Correspondência avaliará primeiro a contagem de parâmetros. Se houver mais de uma correspondência possível para uma contagem de parâmetros, o tipo de parâmetro é então avaliada e a melhor correspondência é determinada. Se ainda houver ambiguidade depois dessa fase da avaliação, o comportamento do processador XAML será indefinido.  
  
 O `x:FactoryMethod` uso do elemento não é uso do elemento de propriedade no sentido de típico, porque a marcação de diretiva não faz referência a tipo de elemento de objeto recipiente. Espera-se o uso do elemento é menos comum do que o uso do atributo. `x:Arguments` (uso do atributo ou elemento) pode ser usado junto com `x:FactoryMethod` uso do elemento, mas isso não é especificamente mostrado nas seções de uso.  
  
 `x:FactoryMethod` como um elemento deve preceder todos os outros elementos de propriedade, devem preceder qualquer `x:Arguments` também fornecidos como elementos e devem preceder qualquer texto de conteúdo/interna/inicialização de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md)
