---
title: facet
ms.date: 03/30/2017
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
ms.openlocfilehash: 1ac46c882b266fbb73d5c709c9fdf297e2b55b1b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783977"
---
# <a name="facet"></a>facet
Uma *faceta* é usada para adicionar detalhes a uma definição de propriedade de tipo primitivo. Uma definição de [Propriedade](property.md) contém informações sobre o tipo de propriedade, mas geralmente é necessário mais detalhes. Por exemplo, um tipo de entidade em um modelo conceitual pode ter uma propriedade do tipo `String` cujo valor pode não ser definido como nulo. As facetas permitem que você especifique esse nível de detalhe.  
  
 A tabela a seguir descreve as facetas que são suportadas em EDM.  
  
> [!NOTE]
> Os valores precisos e os comportamentos de facetas são determinados pelo ambiente de tempo de execução usando uma implementação de EDM.  
  
|Aspecto|Descrição|Aplica-se a|  
|-----------|-----------------|----------------|  
|`Collation`|Especifica a sequência de agrupamento (ou sequência de classificação) a ser usadas para executar a comparação e em ordenação operações em valores de propriedade.|`String`|  
|`ConcurrencyMode`|Indica que o valor da propriedade deve ser usado para verificação de simultaneidade otimista.|As propriedades do tipo primitivo|  
|`Default`|Especifica o valor de propriedade padrão se nenhum valor é fornecido em cima de instanciação.|As propriedades do tipo primitivo|  
|`FixedLength`|Especifica se o comprimento do valor da propriedade pode variar.|`Binary`, `String`|  
|`MaxLength`|Especifica o comprimento máximo de valor de propriedade.|`Binary`, `String`|  
|`Nullable`|Especifica se a propriedade pode ter um valor nulo.|As propriedades do tipo primitivo|  
|`Precision`|Para propriedades de tipo `Decimal`, especifica o número de dígitos que um valor de propriedade pode ter. Para propriedades de tipo `Time`, `DateTime`, e `DateTimeOffset`, especifique o número de dígitos para a parte fracionária de segundos de valor de propriedade.|`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,|  
|`Scale`|Especifica o número de dígitos à direita do ponto decimal para o valor da propriedade.|Decimal|  
|`Unicode`|Indica se o valor da propriedade é armazenado como Unicode.|`String`|  
  
## <a name="example"></a>Exemplo  
 O [Entity Framework ADO.net](./ef/index.md) usa uma DSL (linguagem específica de domínio) chamada[CSDL](./ef/language-reference/csdl-specification.md)(linguagem de definição de esquema conceitual) para definir modelos conceituais. CSDL seguir define um tipo de entidade de `Book` . Observe que as facetas são implementadas como atributos XML. Os valores de aspecto indica que nenhuma propriedade pode ser definida para nulo, e que `Scale` e `Precision` de propriedade de cada `Revision` são definidas como 29.  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>Consulte também

- [Principais conceitos do Modelo de Dados de Entidade](entity-data-model-key-concepts.md)
- [Modelo de Dados de Entidade](entity-data-model.md)
