---
title: 'Como: mapear hierarquias de herança'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: e0ff3fe98fcd9ced0063d2bec85928504ea19bab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743192"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Como: mapear hierarquias de herança
Para implementar o mapeamento de herança em [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], você deve especificar atributos e propriedades de atributo na classe raiz da hierarquia de herança como descrito nas seguintes etapas. Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para mapear hierarquias de herança. Confira [Como Configurar a herança usando o Designer Relacional de Objetos](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  Qualquer atributo ou propriedade de especial são necessários nas subclasses. Observe que as subclasses especialmente não têm o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> .  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Para mapear uma hierarquia de herança  
  
1. Adicione o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> a classe raiz.  
  
2. Também à classe raiz, adicione um atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> para cada classe na estrutura da hierarquia.  
  
3. Para cada atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , defina uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
     Esta propriedade contém um valor que pareça na tabela de base de dados na coluna de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para indicar que a classe ou da subclasse esta linha de dados pertencem.  
  
4. Para cada atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , também adicionar uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> .  
  
     Esta propriedade contém um valor que especifica que a classe ou da subclasse o valor da chave significa.  
  
5. Em apenas um dos atributos de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , adicione uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> .  
  
     Esta propriedade serve para designar uma *fallback* mapeamento quando o valor do discriminador da tabela de banco de dados não corresponde a nenhum <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valor nos mapeamentos de herança.  
  
6. Adicione uma propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para um atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
     Esta propriedade significa que esta é a coluna que contém o valor de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
## <a name="example"></a>Exemplo  
  
> [!NOTE]
>  Se você estiver usando o Visual Studio, você pode usar o Object Relational Designer para configurar a herança. Confira [Como Configurar a herança usando o Designer Relacional de Objetos](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 No exemplo de código, `Vehicle` é definido como a classe raiz, e as etapas anteriores foram implementadas para descrever a hierarquia para [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [Suporte à herança](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [Como: Personalizar Classes de entidade usando o Editor de código](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
