---
title: Diretiva x:FactoryMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58349c5440d0062c64346933e48b64de6c4c7b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xfactorymethod-directive"></a>Diretiva x:FactoryMethod
Especifica um método diferente de um construtor que um processador XAML deve usar para inicializar um objeto depois de resolver o tipo de backup.  
  
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
|`methodname`|O nome do método de cadeia de caracteres de um método de chamada de processadores XAML para inicializar a instância especificada como `object`. Consulte Observações.|  
|`oneOrMoreObjectElements`|Um ou mais elementos de objeto para objetos que especificam parâmetros de método de fábrica. A ordem é significativa; Isso significa que a ordem na qual os argumentos devem ser passados para o método de fábrica.|  
  
## <a name="remarks"></a>Comentários  
 Se `methodname` é um método de instância, ele não pode ser qualificado.  
  
 Há suporte para métodos estáticos como métodos de fábrica. Se `methodname` é um método estático, `methodname` é fornecido como um *typeName*. *methodName* combinação, onde *typeName* nomes de classe que define o método de fábrica estáticos. *typeName* podem ser qualificados de prefixo se referindo-se a um tipo em um xmlns mapeado. *typeName* pode ser um tipo diferente `typeof(``object``)`.  
  
 O método de fábrica deve ser um método declarado público do tipo que faz o elemento de objeto relevante.  
  
 O método de fábrica deve retornar uma instância que pode ser atribuído ao objeto relevante. Métodos de fábrica nunca devem retornar nulos.  
  
 `x:Arguments`opera em um princípio da melhor correspondência para assinaturas de métodos de fábrica. Correspondência avalia a contagem de parâmetro primeiro. Se houver mais de uma correspondência possível para uma contagem de parâmetro, tipo de parâmetro é avaliada e melhor correspondência é determinada. Se ainda houver ambiguidade depois dessa fase de avaliação, o comportamento de processador do XAML é indefinido.  
  
 O `x:FactoryMethod` utilização do elemento não é uso de elemento de propriedade no sentido típico, porque a diretiva marcação não faz referência a tipo de elemento de objeto que contém. Espera-se o uso do elemento é menos comum do que o uso do atributo. `x:Arguments`(uso do atributo ou elemento) pode ser usado junto com `x:FactoryMethod` utilização do elemento, mas isso não é especificamente mostrada na seção de uso.  
  
 `x:FactoryMethod`como um elemento deve preceder todos os outros elementos de propriedade, devem preceder qualquer `x:Arguments` também fornecidos como elementos e devem preceder qualquer texto interna/conteúdo/inicialização de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Arguments](../../../docs/framework/xaml-services/x-arguments-directive.md)
