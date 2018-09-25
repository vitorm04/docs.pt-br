---
title: Modelo de Dados de Entidade
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: e76527b497434ada06762fcab931522fffa2a16b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084076"
---
# <a name="entity-data-model"></a>Modelo de Dados de Entidade
O EDM (Modelo de Dados de Entidade) é um conjunto de conceitos que descrevem a estrutura de dados, independentemente do formato armazenado. O EDM pede emprestado o modelo de relacionamento entre entidades descrito por Peter Chen em 1976, mas também cria a partir desse modelo e estende seus usos tradicionais.  
  
 O EDM resolve os desafios que ocorrem de ter dados armazenados em vários formatos. Por exemplo, considere um negócio que armazena dados em bancos de dados relacionais, arquivos de texto, arquivos XML, planilhas e relatórios. Isso representa desafios significativos na modelagem, na criação de aplicativos e no acesso a dados. Ao criar um aplicativo orientado a dados, o desafio é escrever código eficiente e sustentável sem sacrificar o acesso eficiente a dados, o armazenamento e a escalabilidade. Quando os dados têm uma estrutura relacional, o acesso a dados, o armazenamento e a escalabilidade são muito eficientes, mas a escrita de código eficiente e sustentável torna-se mais difícil. Quando os dados têm uma estrutura de objeto, os conflitos são inversos: escrever código eficiente e sustentável sacrifica o acesso a dados eficiente, o armazenamento e a escalabilidade. Mesmo que o equilíbrio correto entre esses conflitos seja encontrado, novos desafios surgem quando os dados são movidos de um formato para outro. O Modelo de Dados de Entidade resolve esses desafios descrevendo a estrutura dos dados em termos de entidades e relacionamentos que são independentes de qualquer esquema de armazenamento. Isso torna o formato de dados armazenado de dados irrelevante para a criação e o desenvolvimento de aplicativos. E, como as entidades e os relacionamentos descrevem a estrutura de dados como é usada em um aplicativo (não o formato armazenado), eles podem evoluir junto com o aplicativo.  
  
 Um `conceptual model` é uma representação específica da estrutura de dados como entidades e relações, e é definido geralmente em um DSL (linguagem específica do domínio) que implementa os conceitos do EDM. [Linguagem de definição de esquema conceitual (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) é um exemplo de tal uma linguagem específica do domínio. Entidades e relacionamentos descritos em um modelo conceitual podem ser consideradas abstrações de objetos e associações em um aplicativo. Isso permite que os desenvolvedores concentrem-se no modelo conceitual sem se preocuparem com o esquema de armazenamento, e permite que eles escrevam o código pensando em eficiência e facilidade de manutenção. Enquanto isso, os designers de esquema de armazenamento podem se concentrar na eficiência de acesso a dados, armazenamento e escalabilidade.  
  
## <a name="in-this-section"></a>Nesta seção  
 Os tópicos nesta seção descrevem os conceitos do Modelo de Dados de Entidade. Qualquer DSL que implemente o EDM deve incluir os conceitos descritos aqui. Observe que o [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) usa CSDL para definir modelos conceituais. Para obter mais informações, consulte [especificação de CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Principais conceitos do Modelo de Dados de Entidade](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Modelo de Dados de Entidade: namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Modelo de Dados de Entidade: tipos de dados primitivos](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Modelo de Dados de Entidade: herança](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [extremidade de associação](../../../../docs/framework/data/adonet/association-end.md)  
  
 [multiplicidade da extremidade da associação](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [conjunto de associações](../../../../docs/framework/data/adonet/association-set.md)  
  
 [extremidade do conjunto de associações](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [tipo de associação](../../../../docs/framework/data/adonet/association-type.md)  
  
 [tipo complexo](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [contêiner de entidade](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [chave de entidade](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [conjunto de entidades](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [tipo de entidade](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [propriedade de chave estrangeira](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [função declarada por modelo](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [função definida pelo modelo](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [propriedade de navegação](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [propriedade](../../../../docs/framework/data/adonet/property.md)  
  
 [restrição de integridade referencial](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Entity Data Model Tools](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)  
 [Visão geral do arquivo. edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Especificação de CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
