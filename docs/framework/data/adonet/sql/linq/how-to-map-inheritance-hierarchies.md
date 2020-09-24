---
title: 'Como: mapear hierarquias de herança'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: c0709fde96a5d2f39f04a08ccd24ddf90c782f30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166411"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Como: mapear hierarquias de herança

Para implementar o mapeamento de herança no LINQ, você deve especificar os atributos e as propriedades de atributo na classe raiz da hierarquia de herança, conforme descrito nas etapas a seguir. Os desenvolvedores que usam o Visual Studio podem usar o Object Relational Designer para mapear hierarquias de herança. Consulte [como: configurar a herança usando o o/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> Qualquer atributo ou propriedade de especial são necessários nas subclasses. Observe que as subclasses especialmente não têm o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> .  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Para mapear uma hierarquia de herança  
  
1. Adicione o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> a classe raiz.  
  
2. Também à classe raiz, adicione um atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> para cada classe na estrutura da hierarquia.  
  
3. Para cada atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , defina uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
     Esta propriedade contém um valor que pareça na tabela de base de dados na coluna de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para indicar que a classe ou da subclasse esta linha de dados pertencem.  
  
4. Para cada atributo de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , também adicionar uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> .  
  
     Esta propriedade contém um valor que especifica que a classe ou da subclasse o valor da chave significa.  
  
5. Em apenas um dos atributos de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> , adicione uma propriedade de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> .  
  
     Essa propriedade serve para designar um mapeamento de *fallback* quando o valor do discriminador da tabela do banco de dados não corresponder a nenhum <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> valor nos mapeamentos de herança.  
  
6. Adicione uma propriedade de <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> para um atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> .  
  
     Esta propriedade significa que esta é a coluna que contém o valor de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> .  
  
## <a name="example"></a>Exemplo  
  
> [!NOTE]
> Se você estiver usando o Visual Studio, poderá usar o Object Relational Designer para configurar a herança. Consulte [como: configurar a herança usando o o/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 No exemplo de código a seguir, `Vehicle` é definido como a classe raiz e as etapas anteriores foram implementadas para descrever a hierarquia do LINQ.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Confira também

- [Suporte à herança](inheritance-support.md)
- [Como: personalizar classes de entidade usando o editor de códigos](how-to-customize-entity-classes-by-using-the-code-editor.md)
