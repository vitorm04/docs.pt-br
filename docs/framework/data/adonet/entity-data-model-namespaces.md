---
title: 'Modelo de Dados de Entidade: Namespaces'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a8629a1f162f5d942390f62d5a2ac20e2135c531
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784008"
---
# <a name="entity-data-model-namespaces"></a>Modelo de Dados de Entidade: Namespaces
Um namespace no Modelo de Dados de Entidade (EDM) é um contêiner abstrato para [tipos de entidade](entity-type.md), [tipos complexos](complex-type.md)e [associações](association-type.md). Namespaces em EDM são semelhantes aos espaços em uma linguagem de programação: fornecem o contexto para os objetos que contêm e fornecem uma maneira de torne os objetos que têm o mesmo nome (mas estão contidos em namespaces diferentes).  
  
## <a name="example"></a>Exemplo  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](./ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais. O seguinte código de CSDL usar um namespace para identificar um tipo que é definido em um modelo conceitual diferente. O exemplo define um tipo de entidade (`Publisher`) que tenha uma propriedade do tipo complexo (`Address`) que é importado do espaço de `ExtendedBooksModel` . Observe que o elemento de `Using` indica que um namespace foi importado. Observe também que o tipo da propriedade de `Address` é definido usando seu nome totalmente qualificado (`ExtendedBooksModel.Address`), indicando que esse tipo está definido no namespace de `ExtendedBooksModel` .  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
