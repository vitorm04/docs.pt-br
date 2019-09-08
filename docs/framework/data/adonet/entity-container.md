---
title: contêiner da entidade
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95740fb9d8b357a4fa160af6fdafb139711283cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795247"
---
# <a name="entity-container"></a>contêiner da entidade
Um *contêiner de entidade* é um agrupamento lógico [de conjuntos de entidades](entity-set.md), conjuntos de [Associação](association-set.md)e importações de [função](model-declared-function.md).  
  
 O seguinte deve ser verdadeiro de um contêiner de entidade definido em um modelo conceitual:  
  
- Pelo menos um contêiner de entidade deve ser definido em cada modelo conceitual.  
  
- O contêiner de entidade deve ter um nome exclusivo dentro de cada modelo conceitual.  
  
 Um contêiner de entidade pode definir os conjuntos de entidades ou conjuntos de associações que usam os tipos de entidade ou as associações definidos em um ou mais namespaces. Para obter mais informações, [consulte modelo de dados de entidade: Namespaces](entity-data-model-namespaces.md).  
  
## <a name="example"></a>Exemplo  
 O diagrama a seguir mostra um modelo conceitual com três tipos de entidade: `Book`, `Publisher`, e `Author`.  Consulte o próximo exemplo para obter mais informações.  
  
 ![Modelo de exemplo com três tipos de entidade](./media/entity-container/example-model-three-entity-types.gif)  
  
 Embora o diagrama não transmite informações do contêiner de entidade, o modelo conceitual deve definir um contêiner de entidade. O [Entity Framework ADO.net](./ef/index.md) usa uma DSL chamada linguagem de definição de esquema conceitual ([CSDL](./ef/language-reference/csdl-specification.md)) para definir modelos conceituais. CSDL seguir define um contêiner de entidade para o modelo conceitual mostrado no diagrama anterior. Observe que o nome de contêiner de entidade é definido em um atributo XML.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
