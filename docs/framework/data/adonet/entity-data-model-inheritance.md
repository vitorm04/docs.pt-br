---
title: 'Modelo de Dados de Entidade: Herança'
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 9f77f2ebb86ea050c124fbd1c6f2b30ed9e75a1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667192"
---
# <a name="entity-data-model-inheritance"></a>Modelo de Dados de Entidade: Herança
Modelo de dados de entidade (EDM) dá suporte a herança para [tipos de entidade](../../../../docs/framework/data/adonet/entity-type.md). Herança em EDM é semelhante à herança para classes em idiomas de programação orientada a objeto. Como com classes em linguagens orientadas a objeto, em um modelo conceitual você pode definir um tipo de entidade (uma *tipo derivado*) que herda de outro tipo de entidade (a *tipo de base*). No entanto, diferentemente das classes em programação orientada a objeto, em um modelo conceitual o tipo derivado herda sempre qualquer os [propriedades](../../../../docs/framework/data/adonet/property.md) e [propriedades de navegação](../../../../docs/framework/data/adonet/navigation-property.md) do tipo base. Você não pode substituir propriedades herdadas em um tipo derivado.  
  
 Em um modelo conceitual você pode criar hierarquias de herança em que um tipo derivado herda de outro tipo derivado. O tipo na parte superior da hierarquia (um tipo na hierarquia que não é um tipo derivado) é chamado de *raiz do tipo*. Em uma hierarquia de herança, a [chave de entidade](../../../../docs/framework/data/adonet/entity-key.md) deve ser definido no tipo de raiz.  
  
 Você não pode criar hierarquias de herança em que um tipo derivado herda de mais de um tipo. Por exemplo, em um modelo conceitual com um tipo de entidade de `Book` , você pode definir tipos derivados `FictionBook` e `NonFictionBook` que cada herda de `Book`. No entanto, você não pode então definir um tipo que herdasse dos tipos de `FictionBook` e de `NonFictionBook` .  
  
## <a name="example"></a>Exemplo  

O diagrama a seguir mostra um modelo conceitual com quatro tipos de entidade: `Book`, `FictionBook`, `Publisher`, e `Author`. O tipo de entidade de `FictionBook` é um tipo derivado, herdando do tipo de entidade de `Book` . O tipo de `FictionBook` herda `ISBN (Key)`, `Title`, e propriedades de `Revision` , e define uma propriedade chamada adicional `Genre`.  
  
 ![Diagrama que mostra um modelo conceitual com quatro tipos de entidade.](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 O [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa uma linguagem específica de domínio (DSL) chamada linguagem de definição de esquema conceitual ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um tipo de entidade, `FictionBook`, que herda do tipo de `Book` (como no diagrama anterior):  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model.md)
