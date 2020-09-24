---
title: 'Como: declarar colunas como membros de classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: e73b017b5a500a8c48b3fe22557f6c6619f3b227
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166344"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="cb257-102">Como: declarar colunas como membros de classe</span><span class="sxs-lookup"><span data-stu-id="cb257-102">How to: Represent Columns as Class Members</span></span>

<span data-ttu-id="cb257-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atributo para associar um campo ou propriedade a uma coluna de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cb257-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="cb257-104">Para mapear um campo ou propriedade a uma coluna de base de dados</span><span class="sxs-lookup"><span data-stu-id="cb257-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="cb257-105">Adicione o atributo de <xref:System.Data.Linq.Mapping.ColumnAttribute> à declaração de propriedade ou campo.</span><span class="sxs-lookup"><span data-stu-id="cb257-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb257-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb257-106">Example</span></span>  

 <span data-ttu-id="cb257-107">O código a seguir mapeia o campo de `CustomerID` na classe de `Customer` para a coluna de `CustomerID` na tabela de base de dados de `Customers` .</span><span class="sxs-lookup"><span data-stu-id="cb257-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="cb257-108">Você não precisa especificar a propriedade de <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> se o nome pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="cb257-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="cb257-109">Se você não especificar um nome, o nome é presumido ser o mesmo nome que a propriedade ou do campo.</span><span class="sxs-lookup"><span data-stu-id="cb257-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb257-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb257-110">See also</span></span>

- [<span data-ttu-id="cb257-111">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cb257-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="cb257-112">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="cb257-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
