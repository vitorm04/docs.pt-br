---
title: 'Modelo de Dados de Entidade: Herança'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 21dbdff63c07dbcdac8de7bf4b3a8e5d0ece7901
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784073"
---
# <a name="entity-data-model-inheritance"></a>Modelo de Dados de Entidade: Herança
O Modelo de Dados de Entidade (EDM) dá suporte à herança para [tipos de entidade](entity-type.md). Herança em EDM é semelhante à herança para classes em idiomas de programação orientada a objeto. Assim como acontece com classes em linguagens orientadas a objeto, em um modelo conceitual, você pode definir um tipo de entidade (um *tipo derivado*) que herda de outro tipo de entidade (o *tipo base*). No entanto, ao contrário das classes na programação orientada a objeto, em um modelo conceitual, o tipo derivado sempre herda todas as [Propriedades](property.md) e [Propriedades de navegação](navigation-property.md) do tipo base. Você não pode substituir propriedades herdadas em um tipo derivado.  
  
 Em um modelo conceitual você pode criar hierarquias de herança em que um tipo derivado herda de outro tipo derivado. O tipo na parte superior da hierarquia (aquele tipo na hierarquia que não é um tipo derivado) é chamado de *tipo raiz*. Em uma hierarquia de herança, a [chave de entidade](entity-key.md) deve ser definida no tipo de raiz.  
  
 Você não pode criar hierarquias de herança em que um tipo derivado herda de mais de um tipo. Por exemplo, em um modelo conceitual com um tipo de entidade de `Book` , você pode definir tipos derivados `FictionBook` e `NonFictionBook` que cada herda de `Book`. No entanto, você não pode então definir um tipo que herdasse dos tipos de `FictionBook` e de `NonFictionBook` .  
  
## <a name="example"></a>Exemplo  

O diagrama a seguir mostra um modelo conceitual com quatro tipos `Book`de `FictionBook`entidade `Publisher`:, `Author`, e. O tipo de entidade de `FictionBook` é um tipo derivado, herdando do tipo de entidade de `Book` . O tipo de `FictionBook` herda `ISBN (Key)`, `Title`, e propriedades de `Revision` , e define uma propriedade chamada adicional `Genre`.  
  
 ![Diagrama que mostra um modelo conceitual com quatro tipos de entidade.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](./ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define um tipo de entidade, `FictionBook`, que herda do tipo de `Book` (como no diagrama anterior):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
