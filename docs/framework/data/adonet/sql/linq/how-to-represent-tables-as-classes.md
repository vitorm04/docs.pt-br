---
title: 'Como: declarar tabelas como classes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: c02922351909b097dc06085eefbcc0f131350505
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166216"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="30910-102">Como: declarar tabelas como classes</span><span class="sxs-lookup"><span data-stu-id="30910-102">How to: Represent Tables as Classes</span></span>

<span data-ttu-id="30910-103">Use o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atributo para designar uma classe como uma classe de entidade associada a uma tabela de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30910-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="30910-104">Para mapear uma classe a uma tabela de base de dados</span><span class="sxs-lookup"><span data-stu-id="30910-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="30910-105">Adicione o atributo de <xref:System.Data.Linq.Mapping.TableAttribute> à declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="30910-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30910-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30910-106">Example</span></span>  

 <span data-ttu-id="30910-107">O código a seguir estabelece a classe de `Customer` como uma classe de entidade que está associada com a tabela de base de dados de `Customers` .</span><span class="sxs-lookup"><span data-stu-id="30910-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="30910-108">Você não precisa especificar a propriedade de <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> se o nome pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="30910-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="30910-109">Se você não especificar um nome, o nome é presumido ser o mesmo nome que a propriedade ou do campo.</span><span class="sxs-lookup"><span data-stu-id="30910-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30910-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="30910-110">See also</span></span>

- [<span data-ttu-id="30910-111">Modelo de objeto LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="30910-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="30910-112">Como: personalizar classes de entidade usando o editor de códigos</span><span class="sxs-lookup"><span data-stu-id="30910-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
