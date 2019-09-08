---
title: 'Como: declarar tabelas como classes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781763"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="e7a6b-102">Como: declarar tabelas como classes</span><span class="sxs-lookup"><span data-stu-id="e7a6b-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="e7a6b-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atributo para designar uma classe como uma classe de entidade associada a uma tabela de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e7a6b-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="e7a6b-104">Para mapear uma classe a uma tabela de base de dados</span><span class="sxs-lookup"><span data-stu-id="e7a6b-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="e7a6b-105">Adicione o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> à declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="e7a6b-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7a6b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7a6b-106">Example</span></span>  
 <span data-ttu-id="e7a6b-107">O código a seguir estabelece a classe de `Customer` como uma classe de entidade que está associada com a tabela de base de dados de `Customers` .</span><span class="sxs-lookup"><span data-stu-id="e7a6b-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="e7a6b-108">Você não precisa especificar a propriedade de <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> se o nome pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="e7a6b-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="e7a6b-109">Se você não especificar um nome, o nome é presumido ser o mesmo nome que a propriedade ou do campo.</span><span class="sxs-lookup"><span data-stu-id="e7a6b-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a6b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7a6b-110">See also</span></span>

- [<span data-ttu-id="e7a6b-111">O modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e7a6b-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="e7a6b-112">Como: Personalizar classes de entidade usando o editor de código</span><span class="sxs-lookup"><span data-stu-id="e7a6b-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
